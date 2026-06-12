---
title: "k3b cancels disc write for varying reasons (too long to include in title)."
date: 2012-04-21
forum: General Help
---

### Post by New00Folder on 2012-04-21
Hi!

I've been using k3b to burn data files to DVDs since quite some time now. It used to work pretty fine till about a week back.

First of all there suddenly appeared a problem with permissions which I promptly solved using the "Setup system permissions" menu. Then it started complaining about buffer underrun and the error message recommended a lower burning speed. (It was set to "auto"). I finally burned the DVD after many trials (reinserting the disc, setting the correct permissions repeatedly), surprisingly, during simulation. I received a variety of errors during the process:

1> buffer underrun, select lower burn speed
2> something about the medium
3> unpatched cdrecord, unknown error number 254.

But the disc turned out to be fine so I forgot the whole issue.

Today, I got the error which complained about unpatched cdrecord so I complied and installed the original cdrtools. I'm still getting the same error when burn speed=4x and buffer under-run error on burn speed=8x or auto.

The cdrecord error message also says something about "... high quality medium" and I did get a new pack of DVDs the day I first experienced these errors. Can it really be something wrong with the discs? The DVDs don't have anything sinister written over them and they are just like my old DVDs.

We can rule out hardware issues because I can burn the same DVDs on my machine when it's running windows.

I would've have attached logs if I knew where they are.

How can I ensure that the only reason causing a disc write failure is a hardware error? Is there such a reliable application for linux?

Thanks.

---

### Post by zero2xiii on 2012-04-21
Hay,

I have had issues with bad lots on DVDs before, so try buying a small pack (only one disc or even just a pack of 10) from somewhere else or of another brand and testing them.

As far as the logs go, I cant seem to find anywhere k3b logs anything to? Curious... However it can be set up:

Open up k3b, goto Settings > Configure k3b > Notification

Select the messages you want logged to a file (I would suggest all of them, to seperate files) then look underneath the list, there is a option "Log to file" tick this and state where the file should be made (Do it in your home directory for easy access)

Once we have an eye on the errors, we can see if we can solve the issue or not.

Cherz

---

### Post by New00Folder on 2012-05-04
Hi zero2xiii!

I tried burning an image to a CD today and I got an error at about 20%.
The first line was "input/output error, not necessarily serious". Second was about "cdrecord unknown error 254". There was a third line saying this kind of error occurs in TAO(can't be sure about this) mode.

The log file has a single line with today's date:-
- KNotify Fri May 4 19:37:41 2012: Finished with errors

I'll try to burn a different DVD sometime, but I don't think anything is wrong with my DVDs because I can burn them without a hitch on my machine when running windows. This also rules out any hardware error.

---

### Post by Gremlinzzz on 2012-05-04
> **New00Folder said:**
> Hi zero2xiii!

I tried burning an image to a CD today and I got an error at about 20%.
The first line was "input/output error, not necessarily serious". Second was about "cdrecord unknown error 254". There was a third line saying this kind of error occurs in TAO(can't be sure about this) mode.

The log file has a single line with today's date:-
- KNotify Fri May 4 19:37:41 2012: Finished with errors

I'll try to burn a different DVD sometime, but I don't think anything is wrong with my DVDs because I can burn them without a hitch on my machine when running windows. This also rules out any hardware error.

did you try burning that particular image using Windows?:popcorn:

---

### Post by New00Folder on 2012-05-04
Actually I did just a while ago and the disc burn failed due to spindle servo failure. That sounds like a hardware issue to me.

---

### Post by oklokl on 2012-05-04
How to find recent
[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

## Burning
cd ~/Downloads
dir

# cdimg.iso

sudo cdrecord -v cdimg.iso



## make
mkisofs -udf -r -V "1234name" -o cdimg.iso /my1234

# -i error


## booting iso make
sudo mkisofs -r -J -l -L -T -V "Redhat6.1" -b images/boot.img -o redhat.iso /Redhat

---

### Post by New00Folder on 2012-05-10
I've tried some more combinations of CD/DVD brands, burning programs and also tried on a different computer. The fact that emerges is that some programs like k3b (imgburn in windows) can't burn certain type of CD/DVDs. The error messages make it seem like there's something wrong with the hardware. But that can not be the case if other programs (like explorer in windows) can burn the same kind of discs on the same drive. This is what happened with me.

The solution would be to use a different program (Ashampoo v8.04 works for me) for burning.

There are many suggestions on the internet like flasing bios, updating firmware/drivers, using costlier discs, etc. but in my opinion these are pointless if the computer has never had any burning issues before. Here I can see only two things going wrong:-

a> The discs are really bad, in which case you wouldn't be able to burn them using any of usual programs.
b> The drive is broken, in which case the only solution is to get a new one.

---

