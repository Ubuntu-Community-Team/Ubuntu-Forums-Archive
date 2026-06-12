---
title: "Digital camera recognition problems"
date: 2011-10-31
forum: General Help
---

### Post by drrdf2 on 2011-10-31
Hi Guys, can anyone help me please with a digital camera recognition problem?  Version 7 recognised my digital camera immediately and I had no problem uploading my photos etc.  Since version 7 was no longer supported and I ugraded my digital camera is not recognised by any of the subsequent versions at all. I have tried loading all the additional related camera apps in the repository, but no success. I cannot get Ubuntu to recognise my camera any more. I now suspect that this is due to a change in the Linux kernel in later versions? (If it ain't broke don't fix it!) 

My camera is an Advent ADE-MP71, with a usb connection. It is recognised by Microsoft XP without any problem, and also some other Linux distros presumably still using an older kernel (including Ubuntu 7). Does anyone know how I can get the latest versions of Ubuntu  since version 7 to recognise my camera please?

---

### Post by Tamlynmac on 2011-10-31
When you plug the camera in does the file browser recognize and mount it? If so, when you left click on the camera, does it show any  folders or files? If it does then the pics (jpg's, jpeg's or whatever  format your camera uses) are stored in one or more of the folders or  sub-folders. On the cameras I've used or accessed the pics are usually  stored in numbered sub-folders.

We stopped using an app to either look at or download the pics long ago  (8.04). Instead we simply use the file browser to copy & paste the  pics into a pic temp folder for assessment. Once pasted into the folder  the pics are much easier to work with and can be viewed by most all  graphic viewers. We also delete the photos on the camera directly out of  the browser. It's quicker and doesn't rely on an app to access the  camera.

Our cameras all have simm cards and we have card readers on our laptops.  Often we just take the card out and pull the pics off it, via the file  browser. Or use the usb cable if one doesn't have a card reader or the  camera doesn't have a card.

Good Luck & hope this helps.

---

### Post by drrdf2 on 2011-11-01
Hi Tamlynmac,  Thanks for your reply. As I said in my post up to version 8 my camera was recognised by Ubuntu without any difficulty. Since then it is not recognised at all when it is plugged into a usb socket. All other usb devices are still recognised, just no longer the camera. Previously it was recognised just like any other usb; now it is not. I know there is no fault in the camera because I have tested it on another PC with version 7 and it is recognised just like normal. I have also got a dual boot with MS XP and that recognises it without any problem. I have another PC running the latest Puppy Linux and that recognises the camera without difficulty. The problem is not relative to any apps for downloading the photos, but just with the usb connection of the camera not being recognised by later Ubuntu versions at all. Indeed the camera displays an error message "usb error" when plugged in after a while of failing to be able to connect.

So the problem is due to something which was changed in Ubuntu since version 7. I suggested it may be the use of a later kernel which has made some change which affects the usb operation? If that is what it is then I need to find some way around this with the current Ubuntu. I have noticed that I do not seem to be alone in this problem, and some other users have reported problems on other sites with getting their digital cameras to work with later Ubuntu versions and its derivations. In fact it might be a Debian change at the root of it?

Has anyone got any idea how I can get around this please? (and please do not suggest going back to using Windoze like my son has proposed, since I hate Windoze!)

---

### Post by rimibchatterjee on 2011-11-02
Same problem here. For some reason my camera's SD card is also not recognised by my laptop's reader since I switched to Ubuntu 11.10. When I first plugged the USB cable in, I once got the error 'Unable to mount camera...Could not lock the camera' , now I get nothing. I was able that time by some fluke to get the camera to open in shotwell, but alas didn't immediately copy and paste my photographs, so now I'm stuck. The camera is a Kodak easyshare Z915. Now when I plug it in nothing happens, no errors, no nothing.

---

### Post by gordintoronto on 2011-11-02
What version of Ubuntu? 

I plug my camera in, then turn it on, and it is usually recognized. Sometimes it isn't, but turning it off and back on works. However, sometimes the camera (Canon D350) crashes, and I have to remove the battery and put it back in. (All this with the USB cable connected.) Then when I turn the camera on, it always seems to work.

---

### Post by drrdf2 on 2011-11-03
Hi Rimibchatterjee and gordintoroonto, thanks for your replies. Since posting last I have discovered the reason for these problems and that these problems with usb-connected digital cameras are quite widespread across most Linux distros now.  The reason seems to be that some changes were made in the later kernels after 2.6.28 which has directly caused these problems. Some with more knowledge of these things than I are claiming that a conflict has resulted between the later kernels and the usb detection routine and camera applications in Linux and that it is this which is causing these problems. Most Linux distros thus seem to be affected; those affected do not include Puppy and certain others which still use an earlier kernel, so as to still be compatible with older PCs.  To make things even more difficult it seems that not all cameras are unrecognised, with later kernels - only some! 

Thus the only solution seems to be to remove the later kernel and install 2.6.28; this is beyond my level of Linux skills however. It is thus all Ubuntu versions after 9.1 which are affected. So if you go back to using 9.1 you will find that your cameras will be recognised again, but of course that version is no longer supported which gives you a problem. What you can therefore do if you have a spare PC is to run Ubuntu 9.1 on that specifically and only to download your photos, then save them to a usb RAM stick and from that import them to your main PC running a later version of Ubuntu. However that is a most unsatisfactory solution. It seems to me to be crazy to make the continuing claims which so many Linux distros do for running on i386 etc., when as they make more and more changes to the kernel this becomes increasingly a lie, because they are neglecting backwards compatibility.  The truth is that distros using kernels after 2.6.28 will increasingly not run with older PCs and older motherboards. 

So, please is there anyone with sufficient knowledge of these things to suggest how this deficiency in later kernels in Ubuntu may be overcome for users?

---

### Post by gordintoronto on 2011-11-03
With all due respect, you have read allegations of something which you don't completely understand. It might be true, maybe not.

I just copied pictures and videos from my still and video cameras into Kubuntu 11.10, which uses the very latest kernel. That makes me think there is more to it than what you have read.

What version of Ubuntu are you using?

If Puppy works, you could boot it from a CD and copy from your camera to your hard drive.

---

### Post by drrdf2 on 2011-11-04
Hi gordintoronto, I apologise if I gave the impression that I understand what the problem is. I don't and that is why I asked for help!  I did not claim categorically that the problem was due to changes in the kernel.  I purely reported that there are statements on various internet sites, made by those with more understanding than I possess in this respect, which seem to postulate that these problems with digital cameras, which were not present with the use of earlier kernels, have something to do with changes to the versions of the kernel since 2.6.28; these could of course be incorrect or conversely they could be correct. From my research there does seem to be a correlation with all the flavours of Linux which I have checked so far (Ubuntu after 9.1, Fedora, Mandriva,Suse, PC Linux, Kubuntu, Xubuntu, Simply Mepis, Zenwalk, Vector,and Puppy) and the use of later kernels resulting in this deficiency. I did also point out that the problem is made more complicated by the fact that not all digital cameras are affected! 

Since you claim that you can upload photos from your digital camera using  Kubuntu 11.10 you are confirming my point.  You clearly have one of the digital cameras not affected by this problem. I am using Ubuntu 11.10 (and have tried both the 32 and 64 bit versions - they both have the same problem as do Kubuntu and Xubuntu). As I have stated the problem commenced after version 9.1 in Ubuntu. 

Using Puppy on CD as a supposed solution is just like running Ubuntu 9.1 on a spare PC just to download photos. It is not really a solution to the problem. By the way I have just discovered that the latest release of BSD and PCBSD do not suffer from this problem. So one solution is to use BSD rather than Ubuntu until the problem is solved; however, in my opinion the GUI of PCBSD is very inferior to that of Ubuntu.

---

