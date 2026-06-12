---
title: "pidgin"
date: 2010-03-18
forum: General Help
---

### Post by nischalinn on 2010-03-18
I can not connect to yahoo messenger via pidgin, why?

---

### Post by _h_ on 2010-03-18
Yahoo Messenger might be having problems?

---

### Post by nischalinn on 2010-03-18
I think that is not the case because I can chat through yahoo mail. but my pidgin is not opening,why?

---

### Post by l4zy on 2010-03-18
See if you network-manager is working properly. Try stopping it.

---

### Post by howefield on 2010-03-18
> **nischalinn said:**
> I can not connect to yahoo messenger via pidgin, why?

Is this something that just started happening, ie, it was working and is now not working and are you using the current version of Pidgin ?

---

### Post by nightwolf2k5 on 2010-03-18
you could try a different chatting client (like empathy) and see what happens.

---

### Post by linden940 on 2010-03-18
did you delete the the data for the yahoo acct and redid it? if not try that and see if it works or not

---

### Post by nischalinn on 2010-03-18
I've uninstalled the pidgin and again re-install it. But its still not working.

---

### Post by linden940 on 2010-03-18
can you sign into your e-mail address? maybe its closed?

---

### Post by nischalinn on 2010-03-19
I am using pidgin2.5.2. I can not connect to my **yahoo via pidgin**. The problem started from 4 days. When I ping to  **ping scs.msg.yahoo.com, **its work well. but the status bar always shows connecting message. I've reinstalled it, but the problem is still there. I even checked the option in buddies->show, but the status bar still shows connecting message.

When I do "**join a chat**"it shows my account, but the message in the status bar always shows connecting, why?

[FONT=Arial][SIZE=1][COLOR=#000000][FONT=Times New Roman][FONT=Verdana] [/FONT][/FONT][/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=Times New Roman][COLOR=#555555][FONT=Arial][/FONT][/COLOR][/FONT][/COLOR]

---

### Post by _h_ on 2010-03-19
You already have this topic open:

[http://ubuntuforums.org/showthread.php?t=1432824](http://ubuntuforums.org/showthread.php?t=1432824)

---

### Post by nischalinn on 2010-03-19
Ya but I've made my problem more clear this time. So can you fix my prob. now.

---

### Post by cariboo on 2010-03-19
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by zeroseven0183 on 2010-03-19
I do recommend that you get the latest version of Pidgin then let's see what happens. Open a Terminal and copy-paste the following

```

sudo apt-key adv --recv-keys --keyserver  keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
 echo deb  http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

```Then do a
```
sudo apt-get update && sudo apt-get upgrade
``` to upgrade your Pidgin to latest version.

The PPA code is also found in [http://pidgin.im/download/ubuntu](http://pidgin.im/download/ubuntu).

---

### Post by nischalinn on 2010-03-20
I've done 

"sudo apt-key adv --recv-keys --keyserver  keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
 echo deb  [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list"
then 

"sudo apt-get update && sudo apt-get upgrade"

then the last line of the  terminal shows

**0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.**

Now what to do?

---

### Post by nischalinn on 2010-03-20
Thanks to all those who gave me suggestions. Now my pidgin is working.:popcorn:

---

### Post by isbiyanto on 2010-05-06
> **nischalinn said:**
> Thanks to all those who gave me suggestions. Now my pidgin is working.:popcorn:
congratz.... :mrgreen:

---

### Post by eltonw on 2010-05-06
> **nischalinn said:**
> I am using pidgin2.5.2. I can not connect to my **yahoo via pidgin**. The problem started from 4 days. When I ping to  **ping scs.msg.yahoo.com, **its work well. but the status bar always shows connecting message. I've reinstalled it, but the problem is still there. I even checked the option in buddies->show, but the status bar still shows connecting message.

When I do "**join a chat**"it shows my account, but the message in the status bar always shows connecting, why?

[FONT=Arial][SIZE=1][COLOR=#000000][FONT=Times New Roman][FONT=Verdana] [/FONT][/FONT][/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=Times New Roman][COLOR=#555555][FONT=Arial][/FONT][/COLOR][/FONT][/COLOR]

1) If you are connecting to yahoo chat via your browser, it might interpret the access via Pidgin as a second connection to the same account. However, what is more likely is that the same old problem [june 2009] on PIdgin has resurfaced (Yahoo changed something in their security settings). 
So have a look HERE:[http://blog.mypapit.net/2009/06/solving-pidgin-yahoo-messenger-problem.html]("http://blog.mypapit.net/2009/06/solving-pidgin-yahoo-messenger-problem.html")

Also, the **current version **[MAY, 2010] **of Pidgin is 2.6.6**. [COLOR="Red"]For Ubuntu you would have to upgrade per the instructions HERE:[/COLOR]
[http://pidgin.im/download/ubuntu/]("http://pidgin.im/download/ubuntu/")

HTH...

---

