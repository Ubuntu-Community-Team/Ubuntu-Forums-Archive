---
title: "Ubuntu on USB question/explaination"
date: 2009-12-20
forum: General Help
---

### Post by DemiImp on 2009-12-20
So, I've been having a strong urge to try ubuntu, learn it, and eventually get a laptop and put it on it. And I realized I have a usb drive that I could use while I'm at home over the holidays to give me some incentive to learn. I thought everything was fine until I kept reading things like it needing a seperate portion called "casper-rw", which if I understand right is a file on the usb that you can write to so when you restart your computer, anything you put there is saved.
 
But what? This doesn't make a lot of sense to me, not understanding the inside details of what's going on. A usb drive, by definition, is not like a cd. You can create, delete, and modify files to your heart's content. Why can't you install ubuntu on a usb drive that doesn't act like a live cd?
 
Am I missing something? What is going on that causes this seemingly reasonless limitation?

---

### Post by fragos on 2009-12-20
There should be no reason you can't install Ubuntu on a USB disk but to run it from the USB disk you'll need to tell your PC BIOS to try and boot from USB before trying the hard disk. Not all BIOS's provide the ability to boot from USB. You can have many partitions on a physical disk. Linux will look at each partition as if it was a disk.

---

### Post by miniyak on 2009-12-22
demiImp makes a good point

there must be a easy way to do a persistent install on external media...

ive been looking for a week or so and still haven't found a simple way to get a persistent external drive. I have made one but it wasn't simple and involved using an 2.5 enclosure and switching "hard" drives between a notebook and the enclosure. 

I also agree that the concept of a "live" usb is completely redundant when there is write power involved.

the regular installer on the live cd is called ubiquity btw and can be found in the repos, if any one can find a way or knows of a way to get it to run in a regular install plus recognize a second drive as opposed to only the internal one we could probably make some headway here.

---

