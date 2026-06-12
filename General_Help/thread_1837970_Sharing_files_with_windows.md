---
title: "Sharing files with windows"
date: 2011-09-02
forum: General Help
---

### Post by Baloeb on 2011-09-02
What I need is to share files on a windows 7 computer at work and access them on my ubuntu system at home.  What's the best way to accomplish this?  I have dropbox installed at home already.  Is there an easy way to directly access the files, or should I go the dropbox route?

---

### Post by mikewhatever on 2011-09-02
Depending on the environment you work in, it's probably best to talk to the IT staff about a VPN solution.

---

### Post by Baloeb on 2011-09-02
I don't have any of that.  I have one computer at work just hooked up to the internet, and I'd like to access certain folders on it from home.

---

### Post by mikewhatever on 2011-09-02
Well, I guess the most obvious solution would be to enable the Remote Desktop in W7 and then login remotely from home.
[http://www.liberiangeek.net/2011/06/connect-to-windows-7-from-ubuntu-via-remote-desktop-connection/](http://www.liberiangeek.net/2011/06/connect-to-windows-7-from-ubuntu-via-remote-desktop-connection/)

Another way is to use third party application like TeamViewer.

---

### Post by Baloeb on 2011-09-02
Is there a way to do it where I'm not taking complete control of the computer?  There could be staff members who are still using the computer when I want to access files.

---

### Post by mikewhatever on 2011-09-02
> **Baloeb said:**
> Is there a way to do it where I'm not taking complete control of the computer?  There could be staff members who are still using the computer when I want to access files.

Not sure what you mean by complete control. To enable RD in Windows, I'd assume that you'll need admin access. As for who's using the computer at the time you want to remote in, it shouldn't matter, but I'm not expert with W7.

---

### Post by harlequin_ on 2011-09-02
I was able to connect to linux servers at the university using a GUI (I assume that's what is meant by complete control) from my WIN7 system at home using putty and Xming. The other way around must be possible but I am not 100% sure.

edit: If all you need is file sharing then you don't even need to bother with all these. You can setup remote desktop on ubuntu and then in WIN7 using an ssh client (like ssh secure shell) very easily can access your files (with a GUI or terminal if you want).

---

