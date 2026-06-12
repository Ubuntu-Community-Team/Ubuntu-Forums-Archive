---
title: "Libre Office bus error"
date: 2011-10-21
forum: General Help
---

### Post by ngilmour on 2011-10-21
I just upgraded to 11.10 on a Dell Inspiron 1525 laptop.  When I attempt to start Libre Office or when I attempt to open a document that has Libre Office as its default application, the start-up box displays for about twelve seconds, then it disappears, and nothing follows.

When I tried running Libre Office from the terminal, the same thing happened visually, but the terminal displayed "Bus error" without any further explanation.

I've tried un-installing and re-installing Libre Office, but the same thing happens each time.

I do apologize if I'm not following protocol with any part of this thread, and if I need to move it somewhere else, I'd be glad to.

---

### Post by duke.tim on 2011-10-21
This sounds like it is a bug

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

I'm looking through launchpad now to see if it is reported (and any fixes)

---

### Post by duke.tim on 2011-10-21
This looks like there is a bug report for your problem already
[https://answers.launchpad.net/ubuntu/+source/libreoffice/+question/169926](https://answers.launchpad.net/ubuntu/+source/libreoffice/+question/169926)

They ask
"Can you tell us what version of Ubuntu you are using?

Was LibreOffice installed by it? That happens when install 11.04 or you upgrade 10.10 to 11.04. Please tell us which you did."

and they would probably appreciate if you told them you also have this problem. 
:)


It looks like some people running opensuse have the same problem
take a look, seems like they have a 'fix'
[http://forums.opensuse.org/english/get-technical-help-here/applications/458975-libreoffice-3-3-2-doesnt-start.html](http://forums.opensuse.org/english/get-technical-help-here/applications/458975-libreoffice-3-3-2-doesnt-start.html)

---

### Post by ngilmour on 2011-10-21
Thank you much--just posted over there.

---

### Post by jesjep on 2012-02-19
I'd like to bump this one. Upgraded from 11.04 to 11.10 and libreoffice started giving bus error. Guest account didn't help. Also I can't find .libreoffice folder (to be removed) and thus no fix available. Tried uninstall and reinstall to no effect. Basic office tools are very important applications.

---

### Post by duke.tim on 2012-02-19
If you are looking for a a file or folder with a ".", period or end-stop (all the same :) ) make sure that you can view hidden files. 

ctrl+h or select show hidden files under the view menu

also try this if you are trying to completely remove libreoffice

```
sudo apt-get purge libreoffice

```

On the thread issue generally it is a good idea to post in a new thread so that you are more likely to get attention to help fix the problem. It also might attract the attention of more knowledgeable people on the issue :)

hope this helps

---

### Post by jesjep on 2012-03-03
> **duke.tim said:**
> If you are looking for a a file or folder with a &quot;.&quot;, period or end-stop (all the same :) ) make sure that you can view hidden files. 

ctrl+h or select show hidden files under the view menu

also try this if you are trying to completely remove libreoffice

```
sudo apt-get purge libreoffice

```On the thread issue generally it is a good idea to post in a new thread so that you are more likely to get attention to help fix the problem. It also might attract the attention of more knowledgeable people on the issue :)

hope this helps

 Thanks, however the folder doesn't appear to exist. Purge doesn't help either. Reinstall of OS didn't help. With 11.04 there were no problems.

---

