# Solana PumpFun 土狗币 迷因币 狙击 交易 监控机器人

[![a-striking-product-shot-advertisement-fo-o-V66-Rj-Zk-Sqm-Wjx-1-TJZONQ-RFQCs7jv-SGG3j-Pd-Xp-I-1s-Q.jpg](https://i.postimg.cc/136zNRcY/a-striking-product-shot-advertisement-fo-o-V66-Rj-Zk-Sqm-Wjx-1-TJZONQ-RFQCs7jv-SGG3j-Pd-Xp-I-1s-Q.jpg)](https://postimg.cc/fVzsGNPx)

---

![Build](https://img.shields.io/badge/Built%20with-Python-Blue)![License](https://img.shields.io/badge/license-GNU_General_Public_License-_red.svg)![Stars](https://img.shields.io/github/stars/maurosoria/dirsearch.svg)[![Release](https://img.shields.io/github/release/maurosoria/dirsearch.svg)]()[![Sponsors](https://img.shields.io/github/sponsors/maurosoria)](https://github.com/sponsors/maurosoria)[![Discord](https://img.shields.io/discord/992276296669339678.svg?logo=discord)]()[![Twitter](https://img.shields.io/twitter/follow/_dirsearch?label=Follow)]()

## 📋 目录

- [项目介绍](#项目介绍)
- [环境准备](#环境准备)
- [安装配置](#安装配置)
- [使用指南](#使用指南)
- [配置详解](#配置详解)
- [监控和日志](#监控和日志)
- [常见问题](#常见问题)

## 🎯 项目介绍

这是一个高性能的 **Solana 狙击机器人**，专门用于在 PumpFun 和 Raydium 平台上自动狙击新代币。机器人具有以下特性：

- ⚡ **超快速交易执行** - 在 Solana 区块链上实现毫秒级响应
- 🎯 **自动狙击** - 自动检测新代币池并快速买入
- 🔧 **可定制策略** - 支持多种交易策略（泵检测、MEV等）
- 🔗 **DEX 集成** - 支持 Jito、Nozomi 等多个 MEV 服务
- 🛡️ **安全机制** - 支持黑名单/白名单功能
- 📊 **全面监控** - 详细的日志记录和监控
- ⚙️ **易于配置** - 通过环境变量文件配置

## 🛠️ 环境准备

### 系统要求

- **操作系统**: Windows 10/11, macOS, Linux
- **内存**: 至少 2GB RAM
- **网络**: 稳定的互联网连接
- **存储**: 至少 1GB 可用空间

### 必需软件

1. **Rust 环境** (最新稳定版)
2. **Solana CLI 工具**

现在有几种安装方法可选：

**方法 1: 新的官方安装脚本（推荐）**

```bash
# 安装最新稳定版
sh -c "$(curl -sSfL https://release.anza.xyz/stable/install)"
```

**方法 2: 快速安装脚本**

```bash
# 一键安装所有依赖（Mac/Linux）
curl --proto '=https' --tlsv1.2 -sSfL https://solana-install.solana.workers.dev | bash
```

**方法 3: 手动下载二进制文件**

- 访问 [Agave GitHub Releases](https://github.com/anza-xyz/agave/releases/latest)
- 下载对应系统的二进制文件
- 解压并添加到 PATH

**方法 4: 使用 mucho 工具（现代化方法）**

```bash
# 安装所有 Solana 开发工具
npx -y mucho@latest install
```

3. **Git**

## 📦 安装配置

### 1. 克隆项目

```bash
git clone https://github.com/r97-d4/PumpFun-Raydium-sol-.git
cd PumpFun-Raydium-sol-
```

### 2. 创建环境配置文件

在项目根目录创建 `.env` 文件：

```env
# ===== 必需配置 =====
# Yellowstone gRPC 配置
YELLOWSTONE_GRPC_HTTP=https://grpc-n.erpc.global
YELLOWSTONE_GRPC_TOKEN=你的yellowstone_token

# RPC 配置
RPC_HTTP=https://api.mainnet-beta.solana.com

# 钱包配置
PRIVATE_KEY=你的钱包私钥

# ===== 交易配置 =====
# 滑点设置 (建议: 5-20)
SLIPPAGE=10

# 交易计数器限制
COUNTER=100

# 开发者买入数量限制
MAX_DEV_BUY=1000
MIN_DEV_BUY=1

# 每次交易数量 (SOL)
TOKEN_AMOUNT=0.001

# 超时时间 (秒)
TIME_EXCEED=5

# ===== MEV 服务配置 =====
# Jito 服务
JITO_BLOCK_ENGINE_URL=https://jito-api.mainnet.jito.network
JITO_TIP_VALUE=0.0001
JITO_PRIORITY_FEE=1000

# ZeroSlot 服务
ZERO_SLOT_URL=https://api.zeroslot.com
ZERO_SLOT_TIP_VALUE=0.0001

# Nozomi 服务
NOZOMI_URL=https://api.nozomi.com
NOZOMI_TIP_VALUE=0.0001
```

### 3. 编译项目

```bash
# 编译项目
cargo build --release

# 或者开发模式编译
cargo build
```

## 🚀 使用指南

### 1. 获取必要的 Token

#### Yellowstone gRPC Token

1. 访问 Yellowstone 官网
2. 注册账户并获取免费的 gRPC token
3. 将 token 添加到 `.env` 文件

#### 钱包私钥

1. 从你的 Solana 钱包导出私钥
2. 确保钱包中有足够的 SOL (建议至少 0.1 SOL)
3. 将私钥添加到 `.env` 文件

### 2. 启动机器人

```bash
# 发布模式运行
cargo run --release

# 开发模式运行
cargo run
```

### 3. 监控运行状态

启动后，你应该看到类似输出：

```
[INFO] 正在连接 Yellowstone gRPC...
[INFO] 连接成功，开始监控新代币...
[INFO] 检测到新代币池: ABC123...
[INFO] 执行买入交易...
[SUCCESS] 交易成功: 0.001 SOL -> 1000 ABC
```

## ⚙️ 配置详解

### 核心配置参数

| 参数 | 说明 | 建议值 | 风险等级 |
|------|------|--------|----------|
| SLIPPAGE | 滑点百分比 | 5-20 | 高 |
| TOKEN_AMOUNT | 每次交易数量 | 0.001-0.01 | 中 |
| TIME_EXCEED | 超时时间(秒) | 5-10 | 低 |
| MAX_DEV_BUY | 最大开发者买入 | 1000 | 中 |
| MIN_DEV_BUY | 最小开发者买入 | 1 | 低 |

### 高级配置

#### 1. 滑点设置

```env
# 低风险设置
SLIPPAGE=5

# 平衡设置
SLIPPAGE=10

# 高风险设置 (谨慎使用)
SLIPPAGE=20
```

#### 2. 交易数量设置

```env
# 小额测试
TOKEN_AMOUNT=0.001

# 正常交易
TOKEN_AMOUNT=0.01

# 大额交易 (谨慎使用)
TOKEN_AMOUNT=0.1
```

#### 3. 超时设置

```env
# 快速响应
TIME_EXCEED=3

# 平衡设置
TIME_EXCEED=5

# 保守设置
TIME_EXCEED=10
```

## 📊 监控和日志

### 成功交易示例

```
[2024-01-15 10:30:15] [INFO] 检测到新代币: ABC123DEF456
[2024-01-15 10:30:15] [INFO] 开发者买入数量: 500 SOL (符合条件)
[2024-01-15 10:30:16] [SUCCESS] 交易执行成功
[2024-01-15 10:30:16] [INFO] 交易哈希: 7x8y9z...
[2024-01-15 10:30:16] [INFO] 购买数量: 0.001 SOL
[2024-01-15 10:30:16] [INFO] 获得代币: 1000 ABC
```

### 错误日志示例

```
[2024-01-15 10:35:20] [ERROR] 交易失败: 滑点过高
[2024-01-15 10:35:20] [WARN] 重试交易...
[2024-01-15 10:35:21] [ERROR] 钱包余额不足
```

## ❗ 常见问题

### 1. 程序启动后立即退出

**原因**: gRPC 连接失败或配置错误

**解决方案**:

- 检查网络连接
- 验证 Yellowstone token 是否有效
- 确认环境变量配置正确

### 2. 钱包余额不足

**原因**: 钱包 SOL 余额低于交易所需

**解决方案**:

- 向钱包转入更多 SOL
- 减少 TOKEN_AMOUNT 设置
- 确保有足够 SOL 支付交易费用

### 3. 没有检测到新代币

**原因**:

- PumpFun 平台暂时没有新代币创建
- 网络连接问题
- 配置参数过于严格

**解决方案**:

- 耐心等待新代币池出现
- 检查网络连接
- 调整配置参数

### 4. 交易失败

**原因**:

- 滑点设置过低
- 网络拥堵
- 代币池流动性不足

**解决方案**:

- 适当提高滑点设置
- 在网络拥堵时暂停使用
- 检查代币池状态

## ⚠️ 风险提示

### 高风险操作

1. **高滑点设置** (>20%) - 可能导致大幅亏损
2. **大额交易** (>0.1 SOL) - 资金风险较高
3. **长时间运行** - 需要持续监控


### 获取帮助

- **GitHub Issues**: 提交问题报告
- **Discord**: 加入社区讨论
- **Telegram**: 获取实时支持

### 有用的链接

- [Yellowstone gRPC](https://yellowstone.com)
- [Solana 文档](https://docs.solana.com)
- [PumpFun 平台](https://pump.fun)

### 备份配置

```bash
# 备份配置文件
cp .env .env.backup
```

---

**⚠️ 重要提醒**: 加密货币交易存在高风险，请谨慎使用本工具，仅投入你能承受损失的资金。
