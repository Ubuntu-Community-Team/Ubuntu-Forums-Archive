---
title: "Firefox, gnome panel wig out, then  drive gone!"
date: 2010-05-18
forum: General Help
---

### Post by bigsmitty64 on 2010-05-18
O.K.
So last night my room mate had a situation. We "fixed" it but I think it's worth a post here because I still don't know the "cause" 

Keep in mind I did not witness this until well into the problem.

He was rolling along on his "fairly basic" Lucid 64 bit desktop. He opened Firefox, and after about 15 seconds or so, Firefox crashed, (closed down completely on it's own).

He clicked on the Firefox icon on the gnome panel but got nothing. After a couple more clicks the icons on the panel turn to x"s (I believe he said red x's) and he could do nothing.

He clicked on the Main menu, got the menu list, but got no response from any of the items (which were now icon free by the way)

So he reboots, and gets no grub menu, just (oh ya, he dual boots, with separate drives by the way) goes straight to windows. Another reboot, still no grub. This is where I join in on the fun.

We check the bios at startup and alas, the Lucid drive is not showing. But booting into windows and looking in the "drive managment" section its there!
(hmmm...not in bios but windows see's it?)

His drive with Lucid shares a single IDE ribbon with the DVD Burner. This is the setup he has used for a long while with know real issues. 

So he unplugs the DVD drive and reboots, now the Lucid drive shows up in bios!
So we try to boot into Lucid, and bingo, theres grub, and it boots into Lucid.

So we THINK (because we took out the old DVD drive and used another one)
that the DVD drive caused all of this. Thats what it seems like anyways, because now all is well, Lucid and windows both boot fine and firefox is good to go as well as the panel issue.  Sound crazy? It does to us! 

If anyone has any input into why this happened, we are all ears!

Thanks,
Smitty

---

### Post by skrap on 2010-05-18
Also having erratic behavior with my Panel.  Please help.

---

### Post by bigsmitty64 on 2010-05-18
I should add that he's got plenty (I believe 4 or 8 g's) of ram.
AMD Quad core CPU
nVidia 9500 gt graphics card

---

### Post by jetsam on 2010-05-19
OK.  Just a complete gut reaction.  It's largely a BIOS issue.  Two confused bootloaders and a BIOS that thinks too highly of itself.  It was one of those "let's try this, and see if it changes something" fixes.  

The only thing you forgot was the victory jig.

Another change that may have allowed for a more extended jig: remove the Windows partition.

But sounds like you got it sorted already, so no need for that, really.

When it comes to windows and linux in the same box, it's like zoo enclosures.  Keep the species separated.  If possible they shouldn't be able to smell each other.  

I keep them on seperate hard drives and use a floppy boot manager to tell the dumb BIOS what's what.  SBM let's me boot from cd, or either the windows drive or the linux drive.  Take out the disk, it boots like a windows box into Windows.  Put the disk in, and pick a drive.  Then grub gets to do its thing.

And bang... there's my desktop...  whichever partition I picked.  The big drive is for Linux.  

The wee lil' one is for XP Pro.  Windows 7, I'm sure I hardly need tell you, was not my idea.

The sanitized fix for your problem would have been change something in the bios setup.  Likely you didn't need to pull hardware, but pulling hardware is fun so...

Well done.

---

