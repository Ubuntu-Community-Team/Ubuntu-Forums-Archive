---
title: "prepare partitions help pls"
date: 2009-08-25
forum: General Help
---

### Post by bryans44 on 2009-08-25
hey all im new and i want to install ubuntu linux on the side so i still want windows so i want to install linux but not get rid of windows i still want windows to.

im in the installation procces page 4 of 7 i think and the title is prepare partitions and i have no idea what to do with my drives or w/e can anyone tell me what to do? i was thinking of giving my ubuntu 15 gigs of space but i dont know how to do that or what to do pls keep in mind that i dont want to get rid of windows i want to have both 
\thanks!

---

### Post by tgeer43 on 2009-08-25
Here's what you do:

Page 4 of the installation process is titled "Preparing the disk" or something similar. You are now in the disk partitioner. The first bar represents your current partitioning scheme and it should indicate that Windows is currently installed.

Choose the first option which is to install them side by side, choosing between each on startup. The bottom bar represents the new partitioning scheme. Grab the slider with your mouse and drag it to the left to increase the size of the new Ubuntu partition to whatever you want. The legend just below the bar will change to indicate the amount of space you are alloting to Ubuntu as well as how much space will be left for Windows.

When everything looks the way you want it to then just proceed with the rest of the installation. If done correctly this will not interfere with your current Windows installation and when you boot up a Grub menu will appear allowing you to choose to boot into Windows or Ubuntu.

Hope this helps,

tgeer

p.s. In the future a little bit of punctuation, capitalization and spell checking will go a long way towards making your posts more readable.

---

### Post by bryans44 on 2009-08-25
hey i still dont know what to do it says theirs 3 devices /dev/sda, /dev/sda1,/dev/sda2 i dont know what to put in either one of them pls help and it asks me something about swap space or somth and when i try to install it it says something about my cd rom im so confused :(

---

### Post by tgeer43 on 2009-08-25
Okay,

1. Boot all the way into the Live CD without choosing the 'Install' option.

2. Go to System->Administration->Partition Editor and wait for it to scan all of your drives.

3. Leave the partition editor open. Hold down the ALT key while pressing the PrintScreen key. Make note of where it is saving the screenshot file.

4. Post the screenshot back to this thread.

Once I see what your current partitioning scheme is I should be able to better help you.

And for goodness sake, ***please*** take a moment of your time to make your posts readable by humans. There's a reason folks are not lining up to offer their assistance.

tgeer

---

