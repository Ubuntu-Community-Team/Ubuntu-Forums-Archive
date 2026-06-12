---
title: "Skype notifications to XBMC HTTP API"
date: 2010-02-14
forum: General Help
---

### Post by lijcam on 2010-02-14
Hi All,

I'm trying to display skype incomming call notifications within XBMC on both my media centres.

OK background...

So with skype I am using the attached python script to pass Skype notifications to the NotifyOSD in karmic on my laptop. What I would like to do is pass on only incoming call notification to XBMC from the python script.

I have written a shell script to display the notification in XBMC
```
HOSTS='<1st Media Centre> <2nd Media Centre>'

for myHosts in $HOSTS
do
    curl --get "http://$myHosts:8080/xbmcCmds/xbmcHttp?command=ExecBuiltIn(Notification(skype,$1%20calling,5000,skype-icon.png))" -u <username>:<password>

done
```This works however I have no idea how to write python so have no idea how to have the python script execute the shell script with the contracts name as an argument.

So is they anyone out there able to help??

---

