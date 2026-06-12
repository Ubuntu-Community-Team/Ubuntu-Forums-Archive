---
title: "Is UBUNTU Slow?"
date: 2006-01-29
forum: General Help
---

### Post by mishranurag on 2006-01-29
Hi!
When I use some heavier application when some music is playing in rhythmbox, or Kaffeine, the player stops for a while and then comes back. The heavier application which I used was editing the pictures.
My config:
1G RAM, 2.8 GHz Intel pentium 4 and lots of space with space assigned to UBUNTU swap automatically.

Couple of other questions.
My rhythmbox quits unexpectedly many times, is there any solution for that? I like the way Rhythmox lists song. I started using Kaffeine in place of rhythmbox, which is good but it doesn't show genre tab.
Is there any extension, by which I can edit ID3 tag of music files in these players itself.

Thanks in advance for the solution.
Anurag

---

### Post by dcstar on 2006-01-29
[QUOTE=mishranurag]Hi!
When I use some heavier application when some music is playing in rhythmbox, or Kaffeine, the player stops for a while and then comes back. The heavier application which I used was editing the pictures.
......
Thanks in advance for the solution.
Anurag[/QUOTE]
Ubuntu's default file I/O setting is to favour individual applications (which means that they can "hog" disk resources and give the issues you have), you can change this to be more "sharing" by adding the following boot string:

elevator=cfq

For example, my menu.lst entry is:

[I]title		Ubuntu, kernel 2.6.12-10-k7 
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda4 ro quiet **elevator=cfq**
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot[/I]

And if you want this option to "stick" after a kernel upgrade, edit this line as well:
[I]
# nonaltoptions=quiet elevator=cfq[/I]

(Note that I removed the "splash" stuff from my system).

---

### Post by mishranurag on 2006-01-30
Thanks David!

I have done the changes and hope it will be better in my next reboot. Does anybody know the answer of my other two questions regarding Rhythmox and Kaffeine.

Anurag

---

### Post by omegamike on 2006-01-30
Well, even though this isn't a direct answer to your question. I thought I would throw out a suggestion for a good mp3 program. Personally, I use amarok. It has the sorting abilities of Rhythmbox plus lots of other features...which include the ability to edit tags from within the program. I recently bought a bunch of language CD's, and I was able to edit the tags for 100's of tracks from within the program.

---

### Post by mishranurag on 2006-01-30
Thanks Omegamike!
When I tried Amarok first, I didn't like it much, but I tried it again with your recommendation. Its really a wonderful audio player. Thanks a lot for the suggestion. Looks like I am gonna stay with it :)
Anurag

[quote=omegamike]Well, even though this isn't a direct answer to your question. I thought I would throw out a suggestion for a good mp3 program. Personally, I use amarok. It has the sorting abilities of Rhythmbox plus lots of other features...which include the ability to edit tags from within the program. I recently bought a bunch of language CD's, and I was able to edit the tags for 100's of tracks from within the program.[/quote]

---

### Post by towsonu2003 on 2006-01-30
[QUOTE=dcstar]
elevator=cfq

For example, my menu.lst entry is:

[I]title		Ubuntu, kernel 2.6.12-10-k7 
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda4 ro quiet **elevator=cfq**
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot[/I]

And if you want this option to "stick" after a kernel upgrade, edit this line as well:
[I]
# nonaltoptions=quiet elevator=cfq[/I]

(Note that I removed the "splash" stuff from my system).[/QUOTE]
are there any risks (hardware failure, kernel panic, anything) associated with this? purely theoretically speaking, there might be a reason developers did not stick it in as default.

---

### Post by RAOF on 2006-01-30
[QUOTE=towsonu2003]are there any risks (hardware failure, kernel panic, anything) associated with this? purely theoretically speaking, there might be a reason developers did not stick it in as default.[/QUOTE]
I don't belive so.  The reason why it's not the default is probably that it's more suited to a server-type system.  By making sure that no one program hogs the disc, it can make disc access slower if there's only a single program that really needs the disc.

---

