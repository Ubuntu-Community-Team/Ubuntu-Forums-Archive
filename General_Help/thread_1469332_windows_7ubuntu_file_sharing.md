---
title: "windows 7/ubuntu file sharing"
date: 2010-05-02
forum: General Help
---

### Post by Feelin_froggy8877 on 2010-05-02
I have been high and low for the past week trying to find a solution for an issue trying to access shared files on my windows machine. I'm not sure of the last time I was able to access my shared windows files, (before or after upgrade to windows 7). For some reason now, when I open network in ubuntu and try to open my windows shared dir, it asks for user name and pass. I have password off in windows network and sharing and just about anything else I can come across to get access without usr/pass. I have even tried my router wpa credentials. I can access my ubuntu shares just fine from windows. Has anyone alse come across this problem? And if so, any solutions? There was a time I could access my windows shares with no problem.

---

### Post by Tonyaude on 2010-05-10
> **Feelin_froggy8877 said:**
> I have been high and low for the past week trying to find a solution for an issue trying to access shared files on my windows machine. I'm not sure of the last time I was able to access my shared windows files, (before or after upgrade to windows 7). For some reason now, when I open network in ubuntu and try to open my windows shared dir, it asks for user name and pass. I have password off in windows network and sharing and just about anything else I can come across to get access without usr/pass. I have even tried my router wpa credentials. I can access my ubuntu shares just fine from windows. Has anyone alse come across this problem? And if so, any solutions? There was a time I could access my windows shares with no problem.

I have spent days trying to solve this problem and followed all the very helpful advice given by DMIZER but eventually traced it to a Windows issue. It seems that - Windows Live ID sign in Asssistant - which almost always gets installed by default with the Office Live add in, messes up SMB sharing see [http://social.technet.microsoft.com/Forums/en/w7itproappcompat/thread/e4fc6ba5-968e-4370-8a5c-680db85d326c](http://social.technet.microsoft.com/Forums/en/w7itproappcompat/thread/e4fc6ba5-968e-4370-8a5c-680db85d326c) Uninstall Windows Live ID sign in Assistant, reboot and it should all work normally. Good luck.

---

