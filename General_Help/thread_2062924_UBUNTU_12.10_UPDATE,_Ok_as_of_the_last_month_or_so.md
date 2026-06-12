---
title: "UBUNTU 12.10 UPDATE, Ok as of the last month or so my 12.04 is freezing"
date: 2012-09-26
forum: General Help
---

### Post by Jon Anderson on 2012-09-26
Will the 12.10 update take care of the freezing, to do that do I have to make a complete install , do I have to reformat , what will I have to do to get a new enough complete install to get rid of this freeze. Any suggestion welcome

---

### Post by HiImTye on 2012-09-26
without knowing what's causing your freezes, it's impossible to answer. I'd look through your log files to see what the culprit might be. your log files will be in /var/log/ (you can use 'Log File Viewer' as well)

---

### Post by cariboo on 2012-09-26
> **Jon Anderson said:**
> Will the 12.10 update take care of the freezing, to do that do I have to make a complete install , do I have to reformat , what will I have to do to get a new enough complete install to get rid of this freeze. Any suggestion welcome

As of right now, you'd be better off diagnosing and repairing your freezing problem. Keep in mind that the interim releases aren't really meant for the average user, as they usually try out new features that will be included in the next LS release, and some of them way not work as expected.

Could you check /var/log/Xorg.0.log, and see if there is anything that looks like it could be a problem.

---

### Post by newb85 on 2012-09-26
Upgrading to 12.10 could take care of the freezing, but likely not.

The issue may be hardware related.

Give more details on what is happening.  When and how often is it freezing?  Is there something that seems to trigger the freeze?  Can you still move the mouse?

---

### Post by Jon Anderson on 2012-09-26
Well I will be in firefox and For a lenth of time , it freezes for about a minute. It seems that CTRL/ALT/F1 then CTRL/ALT/F7 will clear it up a little faster. But maybe not.It will do this in any program that I'm in. So a fresh install won't fix this.

---

### Post by Jon Anderson on 2012-09-26
> **HiImTye said:**
> without knowing what's causing your freezes, it's impossible to answer. I'd look through your log files to see what the culprit might be. your log files will be in /var/log/ (you can use 'Log File Viewer' as well)********************I have no "log file veiwer" unless it is called something else and "/var/log/" I get the answer "this is a program" then what?

---

### Post by Jon Anderson on 2012-09-26
> **cariboo907 said:**
> As of right now, you'd be better off diagnosing and repairing your freezing problem. Keep in mind that the interim releases aren't really meant for the average user, as they usually try out new features that will be included in the next LS release, and some of them way not work as expected.

Could you check /var/log/Xorg.0.log, and see if there is anything that looks like it could be a problem.
************************/var/log/Xorg.0.log I get permission denied.

---

### Post by HiImTye on 2012-09-26
put this into a terminal (ctrl+alt+t):
```
mkdir ~/logs; sudo cp /var/log/*[!1-9].log $HOME/logs/; sudo chown -R $USER $HOME/logs
```
it will ask for your password.
then open 'files' and go to the folder 'logs' and then double click on the logs you want to look at

---

### Post by Jon Anderson on 2012-09-26
> **HiImTye said:**
> put this into a terminal (ctrl+alt+t):
```
mkdir ~/logs; sudo cp /var/log/*[!1-9].log $HOME/logs/; sudo chown -R $USER $HOME/logs
```it will ask for your password.
then open 'files' and go to the folder 'logs' and then double click on the logs you want to look at*********************It asks for my password then just goes back to "jbander@jbander-System-Product-Name:~$"   Is there more then one password?

---

### Post by HiImTye on 2012-09-27
that means that it worked. go to the folder 'logs' in your home folder and your log files will be there, and you will be able to read them

---

### Post by Jon Anderson on 2012-09-27
[QUOTE=HiImTye;12263509]that means that it worked. go to the folder 'logs' in your home folder and your log files will be there, and you will be able to read them[/QUI
I don't get it when i bring up terminal it says" jbander@jbander-System-Product-Name:~$ "I type in what you suggest, Iget"jbander@jbander-System-Product-Name:~$ " as a responce it asks for passward I put it in and it goes to "jbander@jbander-System-Product-Name:~$"

---

### Post by HiImTye on 2012-09-27
it won't give you any feedback unless there's an error. just open 'Files' and go to the folder 'logs' in your home folder.

---

### Post by Jon Anderson on 2012-09-27
> **HiImTye said:**
> it won't give you any feedback unless there's an error. just open 'Files' and go to the folder 'logs' in your home folder. ******************************Ok but there is 14  files in there which one do I look at

---

### Post by HiImTye on 2012-09-27
I would pay special attention to kern.log and the xorg one

---

