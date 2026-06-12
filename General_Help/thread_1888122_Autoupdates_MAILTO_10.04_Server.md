---
title: "Autoupdates MAILTO 10.04 Server"
date: 2011-11-28
forum: General Help
---

### Post by amhainen on 2011-11-28
I have an old Poweredge 750 server that I got for free in my lab. I really want it to automatically do:

```
sudo apt-get -y update && sudo apt-get -y dist-upgrade
```

I had a cronjob setup for a script to that effect. The bummer part was that it didn't autoremove, autoclean, or reboot when reboot was required. It wasn't very successful.

Today I Googled for the topic and found a couple of cool pages:

[LIST]
[*][https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html]("https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html")
[*][http://www.techrepublic.com/article/automatically-update-your-ubuntu-system-with-cron-apt/6310660]("http://www.techrepublic.com/article/automatically-update-your-ubuntu-system-with-cron-apt/6310660")
[/LIST]

I used the reckless approach of sudo apt-get install [everything!]. I have cron-apt on there, and the unattended-upgrades. Do they work together or against each other or just redundant?

The bummer is that I have no feedback to know if they're working. I would love to have the MAILTO or MAILON=Always work. I have Alpine running, but I don't think I have a mail server running on the machine. It sounds almost impossible to setup a mail server.

Can anyone give me some ideas on how to have automatic daily or hourly updates email me (perhaps requiring setup of a mail server) when it runs? Thanks!

---

