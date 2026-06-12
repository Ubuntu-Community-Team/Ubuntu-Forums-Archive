---
title: "Need help installing Lexmark s305 multipurpose machine in 10.4"
date: 2010-12-23
forum: General Help
---

### Post by Total Noob on 2010-12-23
I am a total noob, don't know anything about installing tar based software into my Ubuntu 10.4 set up (a Dell desktop previously running XP).

I want to install a driver for my Lexmark Impact s305 multipurpose machine, using the driver the Lexmark site recommended, but have been completely unsuccessful.

Here's the software by name.

lexmark-inkjet-legacy-1.0-1.i386.deb.sh.tar.gz

I extracted after right clicking on the icon, and that produced this file:

lexmark-inkjet-legacy-1.0-1.i386.deb.sh

I launched that, got past the license agreement, and came up to a screen that said I needed root privileges and asked for an "administrative password."

I only have one password and entered that. It always works installing software via Synaptic or the Ubuntu Software Center, and everywhere else.

Nevertheless, in trying to install this driver, I got this error message: "incorrect password."

I have been unable to get around this despite repeated efforts. The installer software simply won't accept my password and so it won't install the driver.

In researching the issue, I have seen other people complain of the same problem. 

Given that I am a noob at this, have I missed something critical to the install? Does the software just not work (I have heard Lexmark is not too keen on Linux)?

Help! Please, a lifeline.

Thanks.

---

### Post by matt_symes on 2010-12-23
Hi

Run it like this from the terminal (copy and paste below. Make sure you are in the same directory the file is in)

```
sudo ./lexmark-inkjet-legacy-1.0-1.i386.deb.sh 
```then enter your password at the terminal. You will not see it echoed to the screen. This is normal.

Install and enjoy. It is for 9.04 and you are using 10.10 so hopefully it will work but that will install it.

Kind regards

---

### Post by Total Noob on 2010-12-23
Thanks, Matt, but no luck with that at all.

I had the extracted program on the desktop. I launched the terminal from the desktop, and came to a desktop prompt.

I cut and pasted the code sudo ./lexmark-inkjet-legacy-1.0-1.i386.deb.sh as instructed, and entered the password, only to end up with "Command Not Found" or something substantially similar to that.

Was there another mistake, or is the Lexmark driver just dysfunctional?

Thanks.

---

### Post by matt_symes on 2010-12-23
Hi

What you need to do is move to your Desktop directory

```
cd ~/Desktop
```

Then run the command

```
sudo ./lexmark-inkjet-legacy-1.0-1.i386.deb.sh
```

I don't think you are in your desktop directory.I suspect you were still in ~/. I have actually installed it here so i know it works, although i don't have the printer ;)

Check the file is in the directory by going 

```
ls
```

and make sure i have given you the correct file name as there were a number of download options

Kind regards

---

### Post by matt_symes on 2010-12-23
Hi

If you still can't install it type

```

cd ~/Desktop
ls -l
```

That is small L, and post the results back here

Kind regards

---

### Post by Total Noob on 2010-12-23
Thanks Matt.

The instructions were right on, but it turned out the software and the manufacturer had another 2 surprises fro me and other Ubuntu users. 

After I finally got past the issue of the failure to accept the correct password by running the install from terminal rather than using the launcher, the driver failed to install anyway, and I got a different error message indicating I needed a non-JRE driver, which was separately found.

So I got what the manufacturer suggested where it suggested it (after having listened to it and ending up with it wrong the first time), and it turned out to be corrupted.

Ultimately, third try. I got a second version of the second software from somewhere else, followed Matt's instructions using the proper file instead of the first wrong one suggested and it came out OK. The printer seems to work now.

Thanks.

---

### Post by matt_symes on 2010-12-23
Hi

No problem. :) I installed on the non jre driver and that would explain the file name difference. 

I'm glad it's all good.

Could you mark this thread as solved. Help others searching for a solution. 

Kind regards

---

### Post by WRCKID on 2011-10-20
Please, disregard this post. I corrected my mistake. The instructions were right on the money!

---

