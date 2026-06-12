---
title: "Question about an option for dd comand"
date: 2011-07-01
forum: General Help
---

### Post by ClientAlive on 2011-07-01
Hi,

I just saw this in the man page and am wondering about something.

```

 of=FILE write to FILE instead of stdout

```

If I want to recover data from a drive and I don't want to deal with a ton of used space in the raw image, I wonder if I can use that above option to accomplish it. What I'm thinking is to go into that file afterwords and eliminate all zeros. Then take the file and make an image of it (if that's even possible).

I'm not sure if eliminating 'all' zeros wouldn't destroy some data too. Maybe some are part of that data and need to be there. If that's the case I'd need to make a distinction between zeros that are just unused space and ones that are necessarily part of the data?

Can a guy even make an image from a file like that?

Any thoughts on this?

Thanks.

By the way, there's a reason (and a good one) that I want to stick with dd or some other program that is already standard in the o/s. I'm trying to avoid this deal of download this program or that. I'm looking to just use the things they based all those programs off of in the first place.

Thanks
-----------------

Edit:

Also, can tee be used with dd?

---

### Post by FormatSeize on 2011-07-01
> **ClientAlive said:**
> 
 
What I'm thinking is to go into that file afterwords and eliminate all zeros. Then take the file and make an image of it (if that's even possible).
 
I'm not sure if eliminating 'all' zeros wouldn't destroy some data too. Maybe some are part of that data and need to be there. If that's the case I'd need to make a distinction between zeros that are just unused space and ones that are necessarily part of the data?
 
Can a guy even make an image from a file like that?
 
Any thoughts on this?

I'm not very familiar with the ins and outs of what you are doing, but deleting massive amounts of zeros from a file from which you intend to make an image doesn't sound like a very good idea. 
I also saw your other thread, and I am curious; what is this "tons of unused space" that you don't want to have to deal with while recovering files?

---

### Post by ClientAlive on 2011-07-01
> **FormatSeize said:**
> I'm not very familiar with the ins and outs of what you are doing, but deleting massive amounts of zeros from a file from which you intend to make an image doesn't sound like a very good idea. 
I also saw your other thread, and I am curious; what is this "tons of unused space" that you don't want to have to deal with while recovering files?


Well, the issue in general is that when a person uses the disk image route to save and then restore data, they are forced to deal with whatever unused space was on the disk when they restore. This is always an issue and it just sucks. Sorry, but it does. In my specific case, one of the three hard drives I need to recover is an 80 GB drive but only has 3 GB of data actually on it.

Now, I'm also thinking about my customer here. Is it really cool to make him deal with needing an 80 GB space to restore to? The guy isn't even that tech saavy. What's he gonna do if the image contains the whole o/s the system had on it as well as the personal data and all he wants from it is the personal data?

So I'm not getting paid a whole lot for this (actually it's a barter situation) and there's just simply only so much time and effort I'm willing to put into it. While I am committed to doing the job right I can't afford to turn this into something more than it ought to be. I think the minimum of "doing the job right" though, is to at least carve out only the data from the total amount of space.

Now there are other concerns and constraints as well.

~ The equipment I have at my disposal
~ The type of software tools I'm willing to use (and I have my reasons)
~ The time/ effort involved; or, the efficiency factor (running 2 or 3 processes to reach the goal is more expensive than running one (and I'm not talking about money here))
~ The customer's ability to deal with what I hand him in the end

So I would greatly prefer to use only programs that are standard on things I can run live. I don't really want to get into downloading this flashy program and that flashy program and I especially don't want to deal with Windows only programs.

All those 'flashy programs' usually are just using things like dd and rsync and whatever else has been around forever anyway. They just add a gui and some script to the files. Big whoop! If I have to learn something new I'd rather learn the old school stuff that's dependable and doesn't change. That's the stuff I know I can count on and that I know will always be there for me when I need it. Hence the focus on dd.

Maybe everyone would not agree with my view or my position, but it is what it is. Just thought it would be an appropriate time and place to share that with you, in the hope it is of some use to our communication here.

Thanks FormatSeize. I appreciate it man.

---

### Post by adam814 on 2011-07-01
I'm skeptical your drive is "all zeros" except for 3GB of data.  That is of course unless you've previously wiped it with dd.  I don't even know if they are zeroed like that straight from the factory.

You could compress your image though.  It's not perfect, but you might end up with a 5GB or 10GB image instead of 80GB.

```
sudo dd if=/dev/sda bs=8k | gzip -c9 > backup.img.gz
```

---

### Post by ClientAlive on 2011-07-01
Oh-my-goodness. There is such an easier way to do this. It's called using the cp command (or copy and paste). It turns out Linux will mount and access ntfs file systems. For the life of me I don't know why I put myself through all this. Glad I learned something though.

Thanks a whole lot for your help guys.

Have a great weekend!

:)

---

### Post by gizmo720 on 2011-07-01
I know this is solved, but if anyone else wants to do the original idea, if you run: ```
dd if=/dev/zero of=./zero
rm ./zero
```

you can then dd the entire drive, and then gzip will be able to efficiently compress the free space which is now all zeros

---

### Post by ClientAlive on 2011-07-02
> **gizmo720 said:**
> I know this is solved, but if anyone else wants to do the original idea, if you run: ```
dd if=/dev/zero of=./zero
rm ./zero
```

you can then dd the entire drive, and then gzip will be able to efficiently compress the free space which is now all zeros


Is that a line of code you run after making the image, or something you incorporate into the other code for making the image? I guess I'm confused because I don't see an "sda" in there anywhere and I'm trying to figure out how the code might work.

Thanks. I would be extremely interested to know about it. Good lookin' out man!
-----------------------

Edit:

> **gizmo720 said:**
> 
you can then dd the entire drive, and then gzip will be able to efficiently compress the free space which is now all zeros


I get it. Don't know why I didn't see that before. Thanks.

---

### Post by ClientAlive on 2011-07-02
I wonder if a guy could string it all together with pipes or something. Just run one line of code and forget about it until it's done?

Would that be something like:

```

dd if=/dev/zero of=./zero&& rm ./zero | dd if=/dev/sda of=/path/to/destination/filename.img notrunc,noerror [optional bs if desired] | gzip /path/to/destination/filename.img

```

Think that would work?

---

