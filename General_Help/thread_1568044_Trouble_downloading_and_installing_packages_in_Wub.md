---
title: "Trouble downloading and installing packages in Wubi"
date: 2010-09-04
forum: General Help
---

### Post by swilson11235 on 2010-09-04
I am relatively new to Ubuntu 10.04 and just installed it on this computer with Wubi. I had a previous version of Ubuntu on another computer and did some programming on it. My issue is that downloading a software package from the Ubuntu Software Center or the Synaptic Package manager rarely works. The download proceeds at 1000B/sec and when it gets to applying changes, it stalls out. Now, my Internet connection is solid and i can easily stream videos and download files at over 2 MB/sec. Any suggestions for what to do?

---

### Post by Old_Grey_Wolf on 2010-09-04
It may be the server you are downloading from.

Try going to Synaptic Package Manager, then from the menu select Settings > Repositories. When the page opens there should be a pull-down menu labeled "Download from:", select Other..., then click on the button that says "Select Best Server". It will run a test on the servers then suggest one for you to use. After the test finishes, click on the "Choose Server Button". Click on the "Close" button. It will pop up a message telling you to reload the package information. On the Synaptic main window click on the "Reload" icon.

Then try reloading the packages you want.

---

### Post by swilson11235 on 2010-09-07
I've tried that a while back, but I do believe that I have gotten it fixed now. Thanks for the help

---

