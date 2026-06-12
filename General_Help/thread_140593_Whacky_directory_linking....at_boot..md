---
title: "Whacky directory linking....at boot."
date: 2006-03-06
forum: General Help
---

### Post by bb002 on 2006-03-06
Alright I have a bit of an issue. I want to have some fun with file/directory linking but I'm a bit lost. Let me explain :)

I have hoary on my gateway m275. I'm going to install dapper into the 6GB of freespace i have on this drive (that 6GB used to be XP).

My problem lies in the fact that I want to use the same /home partition (that isn't the problem) and use the same username (that's the problem.) I installed breezy on this laptop before in the old 6GB XP partition to have it blow up. Breezy refused to see most of the hardware and after rebooting to hoary i had to clean my home directory with "mv .* ~/bad'. in order to login into my desktop.

Now i wish to install dapper and use same home dir and same username. I've come up with a plan to save the day but I don't know how to make it happen at boot.

PLAN:


have 4 directories: 
one called bb002_data    -- which contains everything not starting with a "."
one called bb002_hoary   -- which has everything hoary and a link to bb002_data
one called bb002_dapper -- which has everything dapper and a link to bb002_data
and a link named bb002   -- which will link to either the hoary or dapper folder.

have three bash script:
named "magicrelink" -- all it does is recreate the bb002 link as proper and chown the bb002_data directory to make sure there are no right issues with my data. this script exists in /home
one script named "dorelink" -- this script exists in /etc/init.d (of both hoary and dapper), runs at boot and pass either "hoary" or "dapper" as proper to /home/magicrelink


I've got everything working so far in a test directory but will it work in real use and how will I add dorelink to the boot process.

[edit]
if this works out I'll give breezy another shot and see if I can get all the hardware to working in breezy.

---

### Post by 4dz0 on 2006-03-06
I'm not really recommending you just go for it with the same user name but I've had this problem before in breezy and when I recently upgraded to dapper I accidently forgot all about the issues with using the same home dir with the same user name. So anyway I proceeded blissfully unaware into the installation only to realise some days later that the installation had succeeded without the need to worry about using the same user name as the previous installation.

Maybe you can find out if this is an issue which has been resolved in dapper.

---

### Post by bb002 on 2006-03-06
If I can get this working in a real situation, this can be applied to any distro I decide to install. I'm trying to make my life a bit easier so I can test other distros, *ubuntu betas, whacky experiments and the like. Without trying to firgure out what username/pass combo belongs to what distro. This may very well be the long and/or hard way but I'm having fun. I'm just stuck at getting my script added to the boot process.

---

