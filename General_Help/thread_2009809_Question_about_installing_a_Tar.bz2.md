---
title: "Question about installing a Tar.bz2"
date: 2012-06-25
forum: General Help
---

### Post by mountainman70 on 2012-06-25
My computer will not run 11.10 so I am stuck at 11.04 until I can afford a better one. Recently I had a  dpkg failure and had to reinstall 11.04. everything works fine except a few of my previous settings no longer work with 11.04. Its no big deal but I would like to get back to the way I had it.
I have a couple of HDs that I have been playing with and trying to learn some new things, I have installed 10.04 on one HD and have all my previous settings. I want to install Firefox 8.0.1 to get back one of my settings and then update to the 13.01 version and then update to 11.04. This a learning experience for me.

I have DLed firefox-8.0.1.tar.bz2 in my download folder.  So I want to know how do I get it to install? If I use the "extract here command" the 8.0.1 folder is there. But it does not install and I still have the one with 10.04. 
Is there a certain way to install a tar.bz2 package?
Thanks

---

### Post by elliotn on 2012-06-25
tar.gz is like rar or zip, u have to extract them and inside u will find the Read me file with all instructions on how to install.

---

### Post by elliotn on 2012-06-25
tar.bz2 is still the same ok

---

### Post by mountainman70 on 2012-06-25
> **elliotn said:**
> tar.gz is like rar or zip, u have to extract them and inside u will find the Read me file with all instructions on how to install.

Thanks for replying. I extracted the firefox-8.0.1.tar.bz2 and checked the firefox folder and there is no "install or Read me" file there.

---

### Post by ~!geek!~ on 2012-06-25
> **mountainman70 said:**
> Thanks for replying. I extracted the firefox-8.0.1.tar.bz2 and checked the firefox folder and there is no "install or Read me" file there.
You have downloaded the firefox binary (most probably).. After you extract  tar.bz2  contents, you can run firefox by just going into the directory say firefox in this case, and executing the command ./firefox & from the terminal.. To install it for other users or to access it follow this link.. 
 [http://www.cyberciti.biz/faq/how-to-install-firefox-20targz-in-linux/](http://www.cyberciti.biz/faq/how-to-install-firefox-20targz-in-linux/)

---

### Post by mountainman70 on 2012-06-25
> **~!geek!~ said:**
> You have downloaded the firefox binary (most probably).. After you extract  tar.bz2  contents, you can run firefox by just going into the directory say firefox in this case, and executing the command ./firefox & from the terminal.. To install it for other users or to access it follow this link.. 
 [http://www.cyberciti.biz/faq/how-to-install-firefox-20targz-in-linux/](http://www.cyberciti.biz/faq/how-to-install-firefox-20targz-in-linux/)

Thanks for the reply. Could not get the commands to work.

I solved my problem by going to the download folder and making a new folder called firefox2. I then downloaded my copy of 8.0.1.tar.bz2 to that folder and used the "extracte here" to that folder and clicked on the firefox exe and then when it opened, I clicked on preference-advance-Update and unchecked firefox update. I now have all functions in the Advance tab. I set it to not notify me of updates because after a few updates it goes to the beta versions.
I then went to my firefox icon at the top and clicked on Properties and set command to (/home/yourname/Desktop/Downloads/firefox2/firefox/firefox. It now opens with 8.0.1. 
There probably is a simpler way to do this but it works for me and I still have all of my settings and bookmarks I had before.
Now I can update ubuntu to 10.10 and then to 11.04.

Thanks to all who replied.

---

