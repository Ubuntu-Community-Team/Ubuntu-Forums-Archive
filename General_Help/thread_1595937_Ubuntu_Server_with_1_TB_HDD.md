---
title: "Ubuntu Server with 1 TB HDD"
date: 2010-10-13
forum: General Help
---

### Post by oomar on 2010-10-13
Ok so I have ubuntu server 10.04 cause i havent updated (is the server update up?) and I need to get off a sound file. The ext. HDD is 1 TB in size with several hundred Gbs already on it. Now, when I plug it in it just sits there with some lights on the front of it going up and down... Is it indexing the drive or somethign or figuring out something about it and its just taking a long time becasue of the size... or is something wrong? 

if something is wrong... how can i fix that?

ive tried df and sudo fdisk -lu and i cant see it.

---

### Post by Sub101 on 2010-10-13
It should not be a size issue. My TB drive is instant.

Are you sure you have mounted it?

---

### Post by oomar on 2010-10-13
i cant mount it if i cant find it...? idk :/ 

i plug it in... then from what i gather i have to find its "name" such as sda1 or sdb1 etc... then mount that. I cant find that name to mount it. lights are blinking so i dont really want to interrupt anything even though it shouldnt hurt it since it shuold just be reading data

---

### Post by Sub101 on 2010-10-13
Oh I see sorry,

Does dmesg give you anything interesting?

One case I know of is the device not getting enough power.

---

### Post by oomar on 2010-10-13
its all filled up with ssh stuff cause im ssh'ing into the server.

and it shouldnt be that since its the plug that came with the HDD. :/ (its plugged into the wall)

---

### Post by corcomp84 on 2010-10-13
I would try booting to a live CD with a GUI and see if you can see it there... if you can then maybe you can mount it with Gparted. That way you can also check for errors..

---

### Post by oomar on 2010-10-13
i just plugged it in again and it worked.... oh the fallibility of electronics.

---

