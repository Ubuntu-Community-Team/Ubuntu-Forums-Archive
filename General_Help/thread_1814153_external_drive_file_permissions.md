---
title: "external drive file permissions"
date: 2011-07-29
forum: General Help
---

### Post by Moonigan on 2011-07-29
so i've a load of 'folders' (directories?) that have different permissions on my external drive since i clean installed ubuntu on my computer (natty/ macbook 2,1). this has meant that i can't either access certain areas or load stuff onto it (running out of space!) because i'm 'not the owner'.
if i've read [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) this page correctly the command i want would be something like

sudo chmod ugo+rwx -R media/mac drive

then again do i want to be using the chown command?

anyway i just don't want to screw anything up

thanks

---

### Post by Theredbaron1834 on 2011-07-29
That is because when you copied the files it kept the original "owner", and that isn't you in the linux sense.

What I would do is open up a root nautilus (by alt+f2 then entering gksu nautilus) then go to the root of the drive. Right click, properties, permissions, change owner to me, and everything else to read and write, and then click apply permissions.

That should let you read/write everything.

---

### Post by tom4everitt on 2011-07-29
Hi, well, using chmod would work, but it seems a little cleaner keeping the permissions and changing the owner to you. 

```

sudo chown -R yourusername:yourusernam /media/mac

```


A few thoughts:
Changing the file permissions would have the advantage that when you connect your drive to a friends computer, the files would be directly accessible. 

You can always access the files and put files on the drive by using sudo. Just open nautilus as root:
```

gksu nautilus (or sudo nautilus)

```
or simply use the cd/ls/cp/mv etc commands together with sudo to move the files were you want them to regardless of owner and permissions (almost).

---

### Post by tom4everitt on 2011-07-29
> **Theredbaron1834 said:**
> That is because when you copied the files it kept the original "owner", and that isn't you in the linux sense.

What I would do is open up a root nautilus (by alt+f2 then entering gksu nautilus) then go to the root of the drive. Right click, properties, permissions, change owner to me, and everything else to read and write, and then click apply permissions.

That should let you read/write everything.

Too slow, damn :P Had no idea you could do this graphically nowadays. Cool!

---

### Post by Theredbaron1834 on 2011-07-29
Haha, well, always a good day when I get to teach a graybeard something.
Nautilus also lets you add advance permissions, but I didn't think that was needed.

---

### Post by tom4everitt on 2011-07-29
Hehehe, it's a good day when I get to be called a graybeard :P Sort of a dream-come-true-experience. hehe

---

### Post by Theredbaron1834 on 2011-07-29
Well, I have only been in nix really for 2 years, and a gui man my whole life, so as a term man, you are a greybeard. 

Glad I could make your dream come true.

---

### Post by Moonigan on 2011-07-29
thanks folks, i tried the nautilus thing before and had difficulties when it came to actually changing the permissions, but might try again or try chown. its odd, never had this issue with mac os or windows. anyway ill wait till back from work and see if something can be done, post again if problems persist

---

### Post by Theredbaron1834 on 2011-07-29
Well, windows and mac are really single user things, where as linux is from the very start a multiuser environment. 

And in order for nautilus to work, you have to be in a root nautilus. The gksu nautilus command I mentioned.

---

### Post by Moonigan on 2011-07-29
so this is annoying. the drive is called "mac drive" and i'm pretty sure it's confusing the system because it's telling me there's 'no such file or directory' as '/media/mac'

...*sigh*

anyone know how i take the space out or clarify the command somehow?

i also tried the gksu nautilus again and it says 'Sorry, could not change the owner of "mac drive": Error setting owner: Read-only file system"

---

### Post by aeiah on 2011-07-29
> **Moonigan said:**
> so this is annoying. the drive is called "mac drive" and i'm pretty sure it's confusing the system because it's telling me there's 'no such file or directory' as '/media/mac'

...*sigh*

anyone know how i take the space out or clarify the command somehow?

i also tried the gksu nautilus again and it says 'Sorry, could not change the owner of "mac drive": Error setting owner: Read-only file system"

you'd have to encapsulate the path in quotes, or use a slash like so:
```

sudo chown -R yourusername:yourusername /media/mac\ drive

```

if this is a mac drive, is the filesystem one that linux supports writing to?

---

### Post by Moonigan on 2011-07-29
ok so it seemed to be working, ran a bunch of script saying, for example,

"chown: changing ownership of `/media/mac drive/macbook/Pictures/Watching_You_by_CrimsonBlush.jpg': Read-only file system"

and it all looks like that. the last part suggests that, indeed, linux may not support writing to it. perhaps i can make a partition for that. but there are folders i can't view either, the situation seems to be completely unchanged in that regard

EDIT i now also have noticed that the smaller partition on the drive, the windows (fat-32 perhaps?) formatted part, can be written on to and has no other permissions problems. thus assuming i have no problems making a partition (going to bed now) that resolves that issue. perhaps there will be a way to move files to the new partition so i can access them?

---

### Post by Theredbaron1834 on 2011-07-29
Can you open up gparted and tell us what file system is used?

---

### Post by Moonigan on 2011-07-30
hfs+ and fat32

and obviously the hfs+ partition is the one causing me difficulty

screenshot should be attached [ATTACH]198847[/ATTACH]

---

### Post by Theredbaron1834 on 2011-07-30
As it is HFS+, the only way to make it read write is to open up osx, as it is an osx filesystem, and go to disk utilities, select your drive, and then turn off journaling. You can find a page to help you do that [here]("https://help.ubuntu.com/community/hfsplus"). 

Once you do that, you can mount the file system read/write and then the previous commands should work.

---

### Post by tom4everitt on 2011-07-30
As a long time Mac user I am well aware of the hfs+ problem. However, I don't think it's quite necessary to disable journaling. The read-only mount mode is choosen when the drive hasn't been unmounted the correct way, as a safety measure (a highly annoying safety measure, if you ask me). For me it has always been enough to just boot OS X, make sure the extra disk gets mounted (which usually happens by itself), and shut down OS X again. 

The negative part is that you will have to do this over again next time your linux crashes (which, of course, never happens since it is soooo stable, lol :P). 

So maybe better turning journaling off once and for all (given that it solves this problem, I never tried it).

---

### Post by Theredbaron1834 on 2011-07-30
I didn't know about that, apple just isn't my thing. Too much $$ for the cpu. The only thing I like about them is there screen's rule.

That is why I stick to fat32 for all my ext drives that connect to other comps. It really is the only truly supported filesystem across all 3 systems.

Or, of you use a win computer, I would say a few mb partition in fat, and the rest in ext2/3. Why have the few mb partition in fat? So you can have keep [this installer]("http://www.fs-driver.org/") with it. It adds ext2/3 support to win.

I have also heard there is some support of ext2 in osx via macfuse and fuse-ext2. But I don't have an apple.


O, and I take it you have crashes in linux? The only time I have ever had that happen, in my 2 years of messing around, is when:
A. I run out of hard drive space. I only have 15gb, and it runs quick.
B. I run out of ram. I sometimes remove my swapspace to give me more drive space, but it does crash if I do too much then.

---

### Post by tom4everitt on 2011-07-31
Alright, yeah, well the osx ext2 support was pretty rudimentary last time I checked.. 

fat32 is great, but extremely annoying when you try to put a big file on it (>4gb) :/ There seems to be no full-featured file system that's universally supported, sadly enough.


Hehe, maybe I'm just to curious :P Perhaps I shouldn't blame Linux for it though... :) (although Linux really is the cause, indirectly, of my curiosity, so...)

---

### Post by Theredbaron1834 on 2011-07-31
Fat64 for the win? At least I hope. There is already a read only kernal module out, and r/w "will" be on osx, if it isn't already. Kinda has to be. Also, with more and more stuff using linux that anybody can use, someone will get a linux r/w one out soonish. I doubt very much that the SDXC group wants to leave nix out of the mix.

---

