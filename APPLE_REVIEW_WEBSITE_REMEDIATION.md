# App Store 审核整改：隐私政策与 EULA 网站内容

## 目标

整改 Apple App Review：

- Guideline 3.1.2(c)：订阅元数据缺少有效 Terms of Use (EULA) 链接及完整订阅说明。
- Guideline 5.6：7 天体验未在购买流程中明确说明，且网站 EULA 误写成试用结束后自动扣费。

本文件供另一个 agent 修改网站项目使用。不要修改 DemoFlow 工程代码，不要自动 commit 或 push。

## 网站项目与文件

网站项目：

```text
/Users/jamie/ClaudeAi/pjln
```

只修改：

```text
/Users/jamie/ClaudeAi/pjln/index.html
/Users/jamie/ClaudeAi/pjln/userAgreement.html
```

## 一、修改 index.html（Privacy Policy）

### 日期

英文改为：

```text
Last updated: September 4, 2026
```

中文改为：

```text
更新日期：2026 年 9 月 4 日
```

### 删除不准确表述

删除或改写以下内容：

- `fully local without any remote server connection`
- `no sensitive permissions`
- `uninstall will erase all records completely`
- `fully complies with GDPR`
- `无服务器、无网络数据上传行为`
- `无敏感权限`
- `卸载即可彻底清空全部记录`
- `无任何数据跨境传输行为`

### 替换为准确的隐私说明

英文至少应表达以下内容：

1. DemoFlow 是 macOS 本地桌面工具，不运营用于收集用户录屏、媒体、屏幕内容、摄像头或麦克风内容的自有服务器。
2. 用户导出的文件保存到用户选择的位置。
3. 使用录屏、摄像头、麦克风、系统音频等功能时，需要用户授予 macOS 对应权限。
4. 应用设置、输出目录书签、订阅状态和一次性 7 天体验记录保存在本地。
5. 匿名安装 ID 和试用时间保存在 macOS Keychain，不由硬件信息生成，也不会由 DemoFlow 上传。
6. 购买和恢复购买通过 Apple StoreKit/App Store 完成，Apple 按其政策处理交易信息。
7. URL 音频提取只在用户主动提供 URL 时访问网络。
8. 系统语言和地区只用于中英文界面选择。
9. 诊断日志保存在本地，不自动上传。
10. 卸载应用不一定删除 Keychain 记录，也不会删除用户导出到自选目录的文件。
11. 提供隐私联系邮箱：`pjln.top@gmail.com`。

中文内容对应翻译即可。页面继续保留中英文切换。

### 功能链接

保留并检查以下链接：

```text
Privacy Policy:
https://pjcycle.github.io/pjln/

Terms of Use (EULA):
https://pjcycle.github.io/pjln/userAgreement

Support:
https://pjcycle.github.io/pjln/support
```

## 二、修改 userAgreement.html（Terms of Use / EULA）

### 页面标题与日期

英文标题：

```text
DemoFlow Terms of Use (EULA)
```

中文标题：

```text
DemoFlow 使用条款（EULA）
```

英文日期：

```text
Last updated: September 4, 2026 | Effective: September 4, 2026
```

中文日期：

```text
更新日期：2026 年 9 月 4 日 | 生效日期：2026 年 9 月 4 日
```

### 订阅价格说明

不要把 USD 固定价格写成所有地区的最终价格。应明确购买页面会显示本地化最终价格、币种和周期。

英文建议：

```text
The purchase screen shows the final price, currency, and billing period before you confirm. Prices may vary by storefront, taxes, and Apple price changes.
```

中文建议：

```text
确认购买前，购买页面会显示最终价格、币种和计费周期。价格可能因商店地区、税费及 Apple 价格调整而变化。
```

方案周期必须清楚：

- `Pro Monthly`：one-month auto-renewing subscription；一个计费月，按月自动续订。
- `Pro Yearly`：one-year auto-renewing subscription；一个计费年，按年自动续订。
- `Pro Lifetime`：one-time purchase，no auto-renewal；一次性买断，非订阅，不自动续订。

### 必须替换第 2.4 节 Free Trials

禁止保留以下含义：

```text
试用结束后 Apple ID 自动扣费
trial converts to a paid subscription
```

英文替换为：

```text
DemoFlow may offer one seven-day promotional experience to eligible users. This experience is a separate, locally recorded DemoFlow benefit: it does not create an Apple auto-renewable subscription, does not require a cancellation, and does not charge your Apple ID. After the experience ends, premium access ends unless you separately choose and confirm a paid plan. Eligibility is limited to one claim per installation identity and the claim record may remain in the macOS Keychain after uninstalling the app.
```

中文替换为：

```text
DemoFlow 可能向符合条件的用户提供一次 7 天独立促销体验。这项体验是 DemoFlow 本地记录的独立福利：不会创建 Apple 自动续订订阅、无需取消，也不会从您的 Apple ID 扣款。体验结束后，高级功能会结束；只有您另行选择并确认付费方案后，才会开始付费订阅。体验资格按安装身份限制为一次，卸载应用后相关记录仍可能保留在 macOS 钥匙串中。
```

### 保留正式订阅的自动续订说明

第 2.3 节需要继续明确：

- 月付和年付是 Apple 自动续订订阅。
- 当前周期结束前至少 24 小时取消。
- Apple ID 会在续订前 24 小时内扣费。
- 用户可在 Apple ID → Subscriptions 中管理或取消。
- Lifetime 是一次性购买，不自动续订。

### Family Sharing 文案

如果 App Store Connect 没有开启 Family Sharing，不要声称支持家庭共享。可将：

```text
subject to Apple's family-sharing rules
遵循 Apple 家庭共享规则
```

改为：

```text
subject to Apple’s applicable account and storefront rules
遵循 Apple 适用的账户和商店规则
```

## 三、URL 验证

修改并部署后，在外网验证：

```bash
curl -I https://pjcycle.github.io/pjln/
curl -I https://pjcycle.github.io/pjln/userAgreement
```

两个地址最终必须返回 `200`。

如果 `/userAgreement` 返回 `404`，二选一：

1. App Store Connect 改用 `https://pjcycle.github.io/pjln/userAgreement.html`；或
2. 新增 `/userAgreement/index.html`，使无扩展名地址可访问。

## 四、App Store Connect 配置

Privacy Policy URL：

```text
https://pjcycle.github.io/pjln/
```

Terms of Use / EULA URL：

```text
https://pjcycle.github.io/pjln/userAgreement
```

同时建议在 App Description 中加入：

```text
Terms of Use (EULA): https://pjcycle.github.io/pjln/userAgreement
```

如果使用自定义 EULA，还要在 App Store Connect 的 EULA 字段中添加自定义条款内容或有效链接。

## 五、回复审核备注

可在 App Review Information 的 Notes 中填写：

```text
The subscription purchase screen now clearly shows each plan title, billing period, localized price, Privacy Policy, and Terms of Use (EULA).

The seven-day experience is a separate local promotional benefit. It does not create an Apple auto-renewable subscription and does not charge the user’s Apple ID. After the experience ends, users must explicitly choose and confirm a paid plan.

Only the Monthly and Yearly plans are Apple auto-renewable subscriptions. A screen recording showing the updated purchase flow is included.
```

## 六、修改后自检

```bash
git -C /Users/jamie/ClaudeAi/pjln diff --check
git -C /Users/jamie/ClaudeAi/pjln status --short
rg -n -i "automatically charged|trial converts|自动扣款|转为付费订阅|uninstall.*erase|无敏感权限|无服务器" /Users/jamie/ClaudeAi/pjln/index.html /Users/jamie/ClaudeAi/pjln/userAgreement.html
```

最后一条命令不应再命中旧的试用自动扣费和不准确隐私声明。

不要修改旧的 `privacy-en.html`、`privacy-zh.html`，除非确认它们也会被 App Store 审核链接访问。
