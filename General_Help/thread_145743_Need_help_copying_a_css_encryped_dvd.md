---
title: "Need help copying a css encryped dvd"
date: 2006-03-16
forum: General Help
---

### Post by hal pacino on 2006-03-16
My friend is making a dvd I'd like to sell. He's putting css on it (it's non-negotiable, please leave it alone). I just wanted to make sure I'd be able to make duplicates on linux (that I can then burn, encryption and all).

In order to put it on my computer I use:
```
dd if=/dev/dvd of=~/dvdimage.iso bs=2048
```

Now i can just burn dvdimage.iso with ```
growisofs -Z /dev/dvd=dvdimage.iso
``` I assume this all I'll need to have a css-encrypted dvd that'll frustrate pirates for endless seconds.

Are there any other commands/problems I should be aware of? Are my dd and growisofs commands correct? Will they work on css dvds?

Anyway I just want to make sure it'll work. Thanks for your help.

---

### Post by NeghVar on 2006-03-16
Quick question, if this is your frineds dvd that you want to sell, why not ask him to supply you with an original copy so you can do it up. Or is this a my 'friend' doesn't know what I'm doing type of thing?

---

### Post by hal pacino on 2006-03-17
I contracted someone to createa dvd for me. I don't know how to put css protection on a disk in linux and moreover it's not my job, because I'm paying my friend to do to author the dvd. I just need to know how to make duplicates of the master. It's at too low  a volume to get it done professionally.

I just need to know how to duplicate a dvd if he puts css-protection on it (which I understand is easy to break... but I have my reasons). 

This is not to be a post on the merits of css, on who should author my dvds, on the meaning of life. I simply want to know how to duplicate this dvd with linux.

Thanks and goodnight.

---

### Post by bjweeks on 2006-03-17
If it's your movie you should have the master...

---

### Post by Ivan Matveich on 2006-03-17
...to write a css key to a dvd-r disc.

---

### Post by hal pacino on 2006-03-18
Okay then, how do I write a css key to a disk on lniux?

But BEFORE ANSWERING THAT, FOR SIMPLICITY'S SAKE ANSWER THE FOLLOWING: will the above-mentioned method work or not?

Please, I'm so sick of linux users on forums who answer everything, but the question asked. This is really really discouraging. I know that it would be much easier to do this all on a mac, but I don't have a Mac and the guy who made the original dvd for us is not going to make us 50 copies. Moreover I need it exactly as he made it. We requested special requirements for menus background music etc. He said he could copy protect it. I just want to be able to make duplicates so we can start selling them.

I really really really do not want to have to respond to anymore irrelevant posts, but if you have the answer to my question please, I'm begging you just respond. No need to be an obfuscating oracle about it. I just need to solve this problem.

If it's not possible, then I need to know that too. So far, I've gotten no helpful information. I know you guys mean well; I really don't think you're being malevolent, but if you want to help please just answer my question. I'm sick of tangets and we need to get this done soon.

Thanks in advance for any (real) help.

---

### Post by DoktorSeven on 2006-03-18
No; CSS-enabled DVDs must use authentication to read sectors (see [here](http://www.tinyted.net/eddie/css_auth.html) for a description).

dd will fail.  As to how to create a new CSS-enabled DVD from an existing one -- not sure.  It's possible to decrypt the video and burn to a non-CSS disk (using dvd::rip or similar), but apparently this isn't what you want...

---

### Post by glaucus on 2006-03-18
You can't. Consumer DVD-Rs can't use CSS. When the DVDs are pressed professionally, a certain sequence is pressed in the first few bytes to tell the DVD player to decrypt the DVD. Consumer DVD-+Rs have the wrong sequence coded in to prevent people from just directly copying the DVDs.

If you want a DVD you can copy without getting them professionally pressed, then you need a Master copy that is NOT CSS, so you can simply copy it bit for bit.

---

### Post by hal pacino on 2006-03-18
Okay.

Thanks much to DoktorSeven and glaucus. Your responses actually helped. I was beginning to question people's literacy skills

Thanks, I suppose this means that the master my friend will give us will not be css encrypted already. The editor said he put some sort of copy protection on there, I just assumed it was css, but I don't know quite what he's using (I suspect he's using consumer DVD-Rs though) Is there a way to verify if he css-ed the disks?

Also we're starting off at a low volume professional pressing probably isn't an option right now.

But thanks so much for your help. It actually orients us to where we need to go.

---

### Post by klahjn on 2006-03-18
In this case where you are needing CSS on your discs, you may want to have a professional pressing.  Basically, if you want the protection that will offer approximately .4 seconds of hassle to the average user, then you will have to have the professionally pressed, and therefore spend more money than you intended to initially.  Otherwise, I would go back to the person making the disc and ask him to reproduce the Disc w/o the CSS protection and save yourself a lot of money by reproducing yourself.  It's kind of an A or B path....personally, i'd ditch the encryption altogether and save myself the money.

---

### Post by bjweeks on 2006-03-18
Cracking css is *yawn* so it is pointless anyways.

---

