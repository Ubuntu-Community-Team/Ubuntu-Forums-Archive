---
title: "ubuntu partition not mounting in Windows XP"
date: 2009-10-06
forum: General Help
---

### Post by bigdee973 on 2009-10-06
i've used ext2ifs and linux reader on windows xp but they keep saying that the disk drive is not formatted, do you want to format now.  i reinstalled the programs etc. and tried many things but it keeps saying the same thing.  Everything was working fine until i had to reinstall ubuntu.  after i installed the first time it kept giving me that message.  and i reinstalled ubuntu again and again a few times also and i still get the same message. any help would be nice thank you.

---

### Post by david davidson on 2009-10-06
EDIT: never mind.

---

### Post by fluffman86 on 2009-10-06
I've never had any luck successfully reading an ext3 partition in Windows with ext2fs.  Maybe it's just me.

Can you maybe boot into Ubuntu and copy/paste the stuff you need into Windows?  Ubuntu can read and write to ntfs fine.

Can you tell us why you need windows to read ext3?  If it's to copy and paste most data, that can easily stay synced up without the hassle.  When I shared a computer with family, I simply used my ~/.mozilla/profile file to point to my Windows firefox profile.  That way they stayed synced up.  And I always placed my .torrent files in the Windows partition, and saved the downloaded files there as well.  That way, when the rest of the family left Windows idle the torrents could pick up where they left off.

---

### Post by bigdee973 on 2009-10-07
> **fluffman86 said:**
> I've never had any luck successfully reading an ext3 partition in Windows with ext2fs.  Maybe it's just me.

Can you maybe boot into Ubuntu and copy/paste the stuff you need into Windows?  Ubuntu can read and write to ntfs fine.

Can you tell us why you need windows to read ext3?  If it's to copy and paste most data, that can easily stay synced up without the hassle.  When I shared a computer with family, I simply used my ~/.mozilla/profile file to point to my Windows firefox profile.  That way they stayed synced up.  And I always placed my .torrent files in the Windows partition, and saved the downloaded files there as well.  That way, when the rest of the family left Windows idle the torrents could pick up where they left off.

Yes i can access Windows partition from ubuntu but not vice versa.  i need windows to read ext3 cuz sometimes when im on windows having to use the programs that only operate on windows ill need a file thats on the ubuntu partition of the harddrive and rebooting and rebooting gets irritating.  Does anyone know how to help with this?

---

### Post by Matt__ on 2009-10-07
I've tried several apps to get windows to view ext3 but none work, either in xp or vista. 
The solution is just to save everything on my 4th partition which is ntfs(1 being windows, 2 ubuntu, 3 linux 'home'folder)

face it-windows is a closed commercial OS and it really dosnt want you reading anything but its own file systems. As soon as I've mastered linux apps and cli I will lose MS forever :)

---

### Post by executorvs on 2009-10-07
I got ifs to work once but it broke later and I never got it going again.
I have more recently had luck with [http://www.ext2fsd.com/](http://www.ext2fsd.com/) has a few more pieces but works better. still have found no solution to mounting ext4 under windows.
give it a try and post back.

---

### Post by bigdee973 on 2009-10-10
> **fluffman86 said:**
> I've never had any luck successfully reading an ext3 partition in Windows with ext2fs.  Maybe it's just me.

Can you maybe boot into Ubuntu and copy/paste the stuff you need into Windows?  Ubuntu can read and write to ntfs fine.

Can you tell us why you need windows to read ext3?  If it's to copy and paste most data, that can easily stay synced up without the hassle.  When I shared a computer with family, I simply used my ~/.mozilla/profile file to point to my Windows firefox profile.  That way they stayed synced up.  And I always placed my .torrent files in the Windows partition, and saved the downloaded files there as well.  That way, when the rest of the family left Windows idle the torrents could pick up where they left off.

how do you sync firefox with windows and ubuntu? what do you do to that file?

---

### Post by bigdee973 on 2009-10-10
> **executorvs said:**
> I got ifs to work once but it broke later and I never got it going again.
I have more recently had luck with [http://www.ext2fsd.com/](http://www.ext2fsd.com/) has a few more pieces but works better. still have found no solution to mounting ext4 under windows.
give it a try and post back.

thank you ima give it a try

---

### Post by theozzlives on 2009-10-10
Are you using ext4, cause there are no Windows drivers yet. You might give [this]("http://ubuntuforums.org/showthread.php?t=1244185") a try. Also, you can sync your FireFox stuff with the X-Marks addon.

---

### Post by bigdee973 on 2009-10-10
> **theozzlives said:**
> Are you using ext4, cause there are no Windows drivers yet.

im using ext3 from what i see. but how do i get ext4? im using ubuntu 9.04 and i installed everything with default settings

---

### Post by theozzlives on 2009-10-10
> **bigdee973 said:**
> im using ext3 from what i see. but how do i get ext4? im using ubuntu 9.04 and i installed everything with default settings

Check my post again, I edited it. The only reliable way I know to get ext4 is to re-install, that's why my root (/) on one box is ext4 and /home is ext3. I tried to convert and wound up with a mess.

---

