# Reddit-Karma-Bot

## How to run the bot

1. Install docker

2. Update the environment variables below with your account info

3. Paste the whole command below into your terminal

```bash
docker build -t=com.mrpowerscripts/mrps/reddit-karma-bot . \
&& mkdir -p ~/reddit-karma-bot/brain \
&& docker run -it \
  -e REDDIT_CLIENT_ID="MyCoolAppClientID" \
  -e REDDIT_SECRET="MyCoolAppSecret" \
  -e REDDIT_USERNAME="MyCoolUserName" \
  -e REDDIT_PASSWORD="MyPasswordForTheUsername" \
  -e REDDIT_USER_AGENT="script by /u/" \
  -p 8080:8080 \
  --mount src=~/reddit-karma-bot,target=/reddit-karma-bot,type=bind \
  com.mrpowerscripts/mrps/reddit-karma-bot
```

You can provide a proxy server for the docker container to connect through

```bash
--e HTTPS_PROXY="https://127.0.0.1:3001"
```

## The deets

- When the docker container is running you can start the bot by browsing to https://127.0.0.1:8080 The default username pass is admin/pass. It will give you an SSL warning because the CA is self-signed. Just click whatever button allowys you to pass through the warning.
- The bot will store all of the stuff in learns in a folder within your home path (~) called `reddit-karma-bot`.
- The bot will wait until it has 50MB worth of material learned before it will start commenting. This can take a while. The logs on the browser will tell you everything that is happening. There will also be a info.log in the `reddit-karma-bot` folder.