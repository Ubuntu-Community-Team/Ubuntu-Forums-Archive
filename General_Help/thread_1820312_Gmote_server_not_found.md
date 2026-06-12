---
title: "Gmote server not found"
date: 2011-08-07
forum: General Help
---

### Post by morad on 2011-08-07
I installed Gmote 2.0 yesterday and it worked like a charm the first time and I could use most of it's features. But then after restarting the computer, I can not get my phone to find the server running on my computer anymore. I have tried whatever that came to my mind but it has not been successful.
The first time, it just found it without any delays, but seems to be unable to do that now. 

I would appreciate any help you may be able to provide

---

### Post by morad on 2011-08-13
Anyone? Any ideas how I might be able to solve this?

---

### Post by mfdc1969 on 2011-10-22
I just had the same experience. Frustrating but I think I can help ...

When I first downloaded the Linux archive from the gmote website I simply selected "Extract Here" and when I found the .sh script I gave it permission and then ran it.

After verifying that I did want the gmote application I copied it from my Downloads folder to another which I use to hold .debs and other packages in case I want them in the future. I did so, thinking the script had installed software in my Ubuntu's system drive ... but I don't think it did.

I think the script just runs the server from the directory where it was extracted - hence it needs the files in the 2 folders shown above it when you view it in file browser.

I too was unable to reconnect my Samsung Galaxy S to the PC running Ubuntu/gmote until I went to the original archive and extracted the contents again. Then I ran the script with a right click from its location alongside the bin and lib folders.

If you're still having troubles try re-extracting the original archive and run the script again. You won't have to change any setings - that's all saved in your home directory.

Good luck - it's a great little application. It allows me to access my desktop's music via wifi all over my house.

---

### Post by morad on 2011-10-23
Thanks for the reply, but I tried it and did not work for me

Could it have something to do with my firewall? I am not sure how to disable it or anything like that.

I tried downloading it and extracting it in the same folder that I run it from, also leaving it in the downloads folder altogether  but even that does not seem to work. 

The phone still can not find the server for some reason

---

### Post by mfdc1969 on 2011-10-24
Might it be an issue with your router/firewall?

I have not set my router to recognize the 2 ports used (8889 & 9901) but I have enabled uPNP in my router's settings. Perhaps that helps?

[See the gmote support page for this citation: ]("http://www.gmote.org/faq#I_m_having_connection_problems_4820460556074977")
   1. (Note, if this doesn't work, you may have to enter the exception in your firewall manually. To do this, make sure to add both GmoteServer.exe AND javaw.exe with the port 8889 and port 9901 as exceptions).

---

