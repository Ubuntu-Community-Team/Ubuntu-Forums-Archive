---
title: "Advice on Partitions"
date: 2012-01-08
forum: General Help
---

### Post by mblack3nd on 2012-01-08
Hello all,

I recently formatted my HDD and am ready to do a fresh install of Ubuntu. I will also later be installing Windows 7 on the side so I want to have that available.

What I am looking to do is have a partition for
1. Windows 7
2. Ubuntu
3. my files partition 
4. I was reading about making /home its own partition to make re-installs easier
5. swap.

with regards to swap, i was reading something about making a swap file instead of a partition but that a partition is better and I didn't really understand the whole swap file bit so I would rather just do that but that leaves me with 5 partitions...any thoughts?

---

### Post by Bucky Ball on 2012-01-08
Install Windows first! You can install it later but it can be a tweaking headache. 

/home on a separate partition and /swap a partition of about 2Gb. My advice would be:

Install Windows
Create an extended partition with the remaining disk space
When installing Ubuntu choose to manually partition when you get to that part of the install
Create /, /home, /swap as logical partitions within the extended one (you can create other partitions too but these three are available as default).

You will see the Windows partition in there (it will be NTFS). Just leave it alone. Any more than four partitions on one physical drive is not possible so the extended is necessary (this will be seen as one partition regardless of how many logical partitions you put inside it). Does 'my files partition' already exist? If not just use /home for that. 

Hope that helps and good luck. ;)

---

### Post by BertN45 on 2012-01-08
"My files" partition must be an ntfs windows partition, otherwise windows gets into problems and can't access those files. You can try to make it your home partition, but I doubt whether that will work. I would leave the home partition with all its hidden configuration files on the linux partition. You do not have to store your files there.

You can simply put all your files on the ntfs partition (my files) in any folder structure with any names you like. So you can use them in both systems. You only have e,g, to tell music players in the preferences menu entry where to find the music collection. You could also create bookmarks for them.

---

### Post by bluexrider on 2012-01-08
Here is how I got mine:

1. Windows
2. Ubuntu
3. /home
4. swap

What else do you need.

---

### Post by mblack3nd on 2012-01-08
Bucky, 

first off, I don't have my copy of Windows yet but I need to install something before I leave the country for a bit so alas!

so you are saying something like:
1 - P - Windows
2 - E
[INDENT][/INDENT]L - /
[INDENT][/INDENT]L - /home
[INDENT][/INDENT]L - swap
3 - P - My files

???

---

### Post by Bucky Ball on 2012-01-08
> **mblack3nd said:**
> 

so you are saying something like:
1 - P - Windows
2 - EL - /L - /homeL - swap
3 - P - My files

???

Yea, something like that. The 'my files partition' can happily live inside the extended partition also, if it doesn't already exist that is. Just leave free space at the beginning of the drive (about 30Gb should be fine for Win7) so you can dump that there when you get it. Windows likes to be first partition, first drive. You can figure how to install it and get grub to find it when you get to that. So, for now;

1 30Gb free space
2 Extended partition including logical partitions /, /home, /swap
3 My files partition

You can, of course, not create the /home partition (it will be in Ubuntu install then basically on / then) and not worry about the extended partition BUT if you break your system and need to reinstall and info you have in your home folders will be killed (a problem if you really can't get in to back them up). ;)

---

### Post by mblack3nd on 2012-01-08
Ok I think I get it...might as well make the /home partition just in case fit hits the shan?

---

### Post by Double.J on 2012-01-08
> **mblack3nd said:**
> Ok I think I get it...might as well make the /home partition just in case fit hits the shan?

It's always useful - at the end of the day by putting everything not windows into an extended partition, you don't have to worry about the number of partitions to the same extent.

however you're home partition can't be ntfs, so what I do is create a very large partition for all my shared data - about half my drive (but I have a lot of OS, yours may be even larger depending on space) formatted as ntfs. then in windows I send the user information and program files there this is very complicated, and you can mess up the update, so I won't post about program files, just move the user accounts by changing their location in properties.

Then I create a new directory called /Data in my Ubuntu and mount the drive here - you'd need to make a etc/fstab entry to auto mount it, but we can cover that when you get there, I'm just setting out what can be done. this way ubuntu can read and write to all your documents, pics, vids etc, windows can read them and their all on a seperate partition to any OS - good news?

I gues the only question that really needs checking is that you havn't bought a drive that uses gpt, or are planning to use gpt instead of mbr? I use gpt for most of my drives, so it's not a problem, but it would affect your formatting and installing 

all the best :)

---

### Post by Bucky Ball on 2012-01-08
Yes, NTFS shared partition is a good idea else you will not be able to access anything on your Ubuntu partitions (EXT* format) from Win7. I have one called Miscellaneous for sharing data between the two (even though I virtually never use Win). You can access anything on the Win partition from Ubuntu though. 

Just a point: If you install ntfs-3g and ntfs-config that will mount all NTFS partitions and re-write the fstab appropriately for you. You don't then need to manually create mount points for your NTFS partitions. Neat. ;)

---

### Post by mblack3nd on 2012-01-08
> **gnu/mirow said:**
> It's always useful - at the end of the day by putting everything not windows into an extended partition, you don't have to worry about the number of partitions to the same extent.

Yeah think I am getting that part

> however you're home partition can't be ntfs, so what I do is create a very large partition for all my shared data - about half my drive (but I have a lot of OS, yours may be even larger depending on space) formatted as ntfs. then in windows I send the user information and program files there this is very complicated, and you can mess up the update, so I won't post about program files, just move the user accounts by changing their location in properties.

Ok, tackle that sucker when it comes though I think saw an explanation of that somewhere...

> Then I create a new directory called /Data in my Ubuntu and mount the drive here - you'd need to make a etc/fstab entry to auto mount it, but we can cover that when you get there, I'm just setting out what can be done. this way ubuntu can read and write to all your documents, pics, vids etc, windows can read them and their all on a seperate partition to any OS - good news?

Yes, great news! That is exactly what I am looking to do.

> I gues the only question that really needs checking is that you havn't bought a drive that uses gpt, or are planning to use gpt instead of mbr? I use gpt for most of my drives, so it's not a problem, but it would affect your formatting and installing 

all the best :)

And here is where I get lost haha...have no idea what gpt means...using a drive that is a couple years old now.

I guess I am looking to keep that /home and /files partitions safe in case of a an issue arising like I had recently. So leave 15 or so at the beginning, create the extended partition and three logical partition there within of /, /home, and /swap and then partition off the rest as a NTFS for the Files partition...did i get that right haha

---

### Post by mblack3nd on 2012-01-08
> **bucky ball said:**
> yes, ntfs shared partition is a good idea else you will not be able to access anything on your ubuntu partitions (ext* format) from win7. I have one called miscellaneous for sharing data between the two (even though i virtually never use win). You can access anything on the win partition from ubuntu though. 

Just a point: If you install ntfs-3g and ntfs-config that will mount all ntfs partitions and re-write the fstab appropriately for you. You don't then need to manually create mount points for your ntfs partitions. Neat. ;)

wooooo hoooooo!!!!!!
:d

---

### Post by Double.J on 2012-01-08
> **mblack3nd said:**
> And here is where I get lost haha...have no idea what gpt means...using a drive that is a couple years old now.

I guess I am looking to keep that /home and /files partitions safe in case of a an issue arising like I had recently. So leave 15 or so at the beginning, create the extended partition and three logical partition there within of /, /home, and /swap and then partition off the rest as a NTFS for the Files partition...did i get that right haha

Ah don't worry, I was jut checking you weren't using a GUID Partition Table instead of MBR - ie if you were using an old mac machine, or a hdd over 2TB!, otherwise it doesn't really matter... scratch that point!

basically yes your logical partition set up sounds spot on... the 15gb windows doesn't - windows is a hog! I did a clean install that munched up 18GB after updates! and ntfs will start slowing down a lot as it gets full.. plus windows will bug you a lot about it! If you can apre the space, 40GB, as a min, 25?

---

### Post by Bucky Ball on 2012-01-08
I would leave more than 15Gb for Win7. Double that. Not sure of the exact requirements but think the OS (without adding programs) needs that much. 

Yea, just looked here:

[http://windows.microsoft.com/en-AU/windows7/products/system-requirements](http://windows.microsoft.com/en-AU/windows7/products/system-requirements)

And just Win7 needs 16Gb available space then you want to add programs (I imagine). Figure what you are going to be using in there then roughly calculate how much space you are going to need. Better bigger than a tight squeeze (and Win7 will crash without some space to work in - they say 16Gb but I bet it runs poorly (if at all) with just 16Gb). I gave it 30Gb and have not much installed besides Win7. XP was more economical and will probably switch to that when I could be bothered doing it. 

> **gnu/mirow said:**
> ... basically yes your logical partition set up sounds spot on... the 15gb  windows doesn't - windows is a hog! I did a clean install that munched  up 18GB after updates! and ntfs will start slowing down a lot as it gets  full.. plus windows will bug you a lot about it! If you can apre the  space, 40GB, as a min, 25?

+1. Beat me to it. I'll second that ... ;)

---

### Post by mblack3nd on 2012-01-08
> **bucky ball said:**
> i would leave more than 15gb for win7. Double that. Not sure of the exact requirements but think the os (without adding programs) needs that much. 

Yea, just looked here:

[http://windows.microsoft.com/en-au/windows7/products/system-requirements](http://windows.microsoft.com/en-au/windows7/products/system-requirements)

and just win7 needs 16gb available space then you want to add programs (i imagine). Figure what you are going to be using in there then roughly calculate how much space you are going to need. Better bigger than a tight squeeze (and win7 will crash without some space to work in - they say 16gb but i bet it runs poorly (if at all) with just 16gb!



+1. Beat me to it. I'll second that ... ;)


got it!!!...thanks so much for your help guys, greatly appreciated!

---

