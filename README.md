# slackcat

A simple way of sending messages from the CLI output to your Slack with webhook.

The goal is to get automated alerts for interesting stuff!

## Installation

- Download a prebuilt binary from [releases page](https://github.com/dwisiswant0/slackcat/releases/latest), unpack and run! or
- If you have go compiler installed: `go get dw1.io/slackcat`

The only dependency of slackcat is Go 1.13.

## Configuration

**Step 1:** Get yours Slack incoming webhook URL [here](https://slack.com/intl/en-id/help/articles/115005265063-Incoming-webhooks-for-Slack).

**Step 2** _(optional)_**:** Set `SLACK_WEBHOOK_URL` environment variable.
```bash
export SLACK_WEBHOOK_URL="https://hooks.slack.com/services/xxx/xxx/xxx"
```

## Usage

### Flags

```
Usage of slackcat:
  -1    Send message line-by-line
  -u string
        Slack Webook URL
  -v    Verbose mode
```

### Basic Usage

```bash
▶ assetfinder dw1.io | anew | slackcat -u https://hooks.slack.com/services/xxx/xxx/xxx
```

The `-u` flag is optional if you've defined `SLACK_WEBHOOK_URL` environment variable.

Slackcat also strips the ANSI colors from stdin to send messages, so you'll receive a clean message on your Slack!

```bash
▶ nuclei -l urls.txt -t cves/ | slackcat
```

### Line-by-line

Use the `-1` flag if you want to send messages on a line by line _(default: false)_.

```bash
▶ assetfinder dw1.io | anew | slackcat -1
```

## Thanks

- Inspired by [rez0](https://twitter.com/rez0__) [article](https://rez0.blog/hacking/2020/02/07/bugbounty-alert-automation-tips.html), that's why this tool was made!
- [acarl005](https://github.com/acarl005) for his awesome stripansi.