---
title: "Suspend mode on Ubuntu 9.10 fails on HP 311 Mini"
date: 2010-01-06
forum: General Help
---

### Post by GPJones on 2010-01-06
Hello to all especially the developers!

Recently I bought an HP Mini 311 and had hoped to place Ubuntu on it and dump Windows entirely. However, I had a couple of glitches. One was the broadcom wireless driver (which I found an answer for and it worked perfectly. Just a couple of lines typed in terminal fixed it).

The second problem is the inability to recover from suspend mode or Windows would call it sleep. I purchased the smaller netbook for the portability and longer battery life. It is extremely aggravating when the suspend function does not work correctly which defeats the longer battery life I had in mind when I purchased the Mini. 

Not being an expert in Ubuntu or Linux I searched these forums in vain to try to find an answer. Ubuntu developers are you listening? This is a big issue and paints an awkward black eye on Unbuntu 9.10.

If there is an answer that is user friendly could someone steer me to it or I ask that this be set as a higher bug in the "to be fixed" list and worthy of an immediate update when done.

Thanks!

---

### Post by amaroKer on 2010-01-26
I'd love to diagnose the problem, but I need to get wireless working on my Mini 311 first.  Do you happen to remember how you got your wireless working?  I can't boot Ubuntu unless I boot with acpi=off in grub.  Perhaps this will help you: [https://help.ubuntu.com/community/SuspendHowto]("https://help.ubuntu.com/community/SuspendHowto") and scroll down to ACPI.  I know it's an old file, so make a backup of the file you're changing.

---

### Post by FireNoodle on 2010-05-15
I have had no problems with suspend on my mini, what errors are you getting?

Enable the broadcom proprietary driver for the wireless. I have had no problems with that either.

---

