---
title: "Unable to use 12.04 software center"
date: 2012-09-27
forum: General Help
---

### Post by cousinlucky on 2012-09-27
After downloading the 135 updates to my new ubuntu 12.04 os I tried to download software from the " Ubuntu Software Center " but nothing I try to downlosd ever downloads. Can anyone please tell me what I need do to make this application work correctly? Thanks!!

---

### Post by daslinkard on 2012-09-27
The first thing that I would suggest doing would be rebooting the machine to see if this fixes the issue.  If you try this and this does not work then the next thing to do would remove the Software Center and then re-install it.



To do that just press>  **Ctrl+Alt+T** on your keyboard to open Terminal. When it opens, run the command below.
```
sudo apt-get purge software-center   
```and when that's done, do```
sudo apt-get install software-center   
```Then do   ```
sudo apt-get update && sudo apt-get upgrade 
```

---

### Post by Bashing-om on 2012-09-27
cousinlucky;

Basics: Any errors generated from the terminal command :
```
sudo apt-get update
```

we will go from that! <==BDQ

---

### Post by cousinlucky on 2012-09-28
I believe my problem with the software center comes from the wvdial that I had to install using the terminal. I had to do that so that I could get onto the internet and download ubunt's 135 files which included Gnomeppp.

I believe that the 12.04 os will not download anything from the software center unless the internet has been accessed by using gnomeppp.

I set up gnomeppp but I always get the message " can not open modem " when I try to use it. Does anyone know how I can resolve this problem? Thanks!

---

### Post by cousinlucky on 2012-09-30
I gave up looking for a way to get dowhloads fron the " software center " and installed synaptic which works just fine.

---

