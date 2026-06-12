---
title: "Ubuntu Studio Install Help"
date: 2012-03-08
forum: General Help
---

### Post by RadicalRebel on 2012-03-08
I am a new user trying to install Ubuntu Studio on my PC. I looked through the forums and tried a "Fresh Install" of Ubuntu Studio using the Ubuntu Studio 11.04 (Natty Narwhal)download from the site  [http://cdimage.ubuntu.com/ubuntustudio/releases/11.04/release/]("http://cdimage.ubuntu.com/ubuntustudio/releases/11.04/release/") 

I burned the 64-bit PC (AMD64)image to a DVD-R and tried to install from the DVD-R. Although when used on my laptop it worked when I entered the GRUB setup to install after choosing an option the screen would simply go blank and nothing would happen. It did not enter the guided setup "wizard" as on the laptop and the Ubuntu Studio Icon was not present, it was a black and white D-OS like GRUB window.
  
I have a Acer Aspire AX3470-EB30P with:
-64-bit Windows 7
-AMD quad-core A6-3600 APU with Radeon HD 6530D graphics
-4GB DDR3 memery
-1TB Hard drive
-DVD super multi drive

Is the hardware not compatible with the version of Ubuntu Studio I was installing??

Just trying to get started so I can dual-boot and use the open source audio and video programs, especially Blender and any audio recording/editing as well as working with VSTs. I have never used Linux in the past but am a fairly advanced Windows user and would love to give Linux a try. 

Thank you for helping a newbie out.

---

### Post by immerohnegott on 2012-03-08
I'd wager it's a hardware compatibility issue, specifically with the integrated graphics on that APU (while the hardware's been out a bit, Ubuntu tends to pick a kernel a couple months before release and stick with that revision, which can cut out some newer hardware). 

You might want to try 11.10 or even the 12.04 beta. Also, just my two cents, I wouldn't bother with Ubuntu Studio. I've been doing audio production stuff on the standard repos (in Ubuntu 11.10 and Mint 11) for a while now. If you so choose, there's a project called KxStudio that hosts a bunch of audio-specific stuff in a set of repos. [http://kxstudio.sourceforge.net]("http://kxstudio.sourceforge.net")

---

### Post by immerohnegott on 2012-03-08
Also, there's a bit of a learning curve for doing audio stuff under Linux (nothing really difficult, just a different way of working with things than under Windows/Mac). Google around or search the forums for some good how-to's on setting up for that sort of thing, or you can send me a message and I can shoot you some probably-correct tips (didn't want to hijack the thread with a lengthy diatribe on audio production).

---

### Post by bcschmerker on 2012-03-08
Ye might have to wait a bit for Precise Pangolin™ (12.03b2-pre as of March 2012) to mature (as 12.04.0-LTS when released to market April 2012) before using it.  I was never able to get the previous-generation realtime kernels (development stopped at 2.6.31-11-rt, while Lucid Lynx™, currently 10.04.4-LTS, was in development) to run reliably on AMD® hardware---I use a hybrid Everex® (orig. a TC2502 with all-VIA® hardware) upgraded with a Gigabyte® GA-MA78GM-S2HP mobo and Advance Micro Devices® Athlon X2 5600+; things have supposedly changed in Precise with a new approach to low-latency and real-time-preemptive code in Kernels 3.0-up.  Precise uses Kernel 3.2.

---

### Post by immerohnegott on 2012-03-08
That bloody RT kernel is most of the reason why I stopped messing with Ubuntu Studio in the first place. Honestly, I haven't noticed any increase in latency or any less responsiveness using the standard kernels in 11.04+ (still setting jack to RT, adding myself to @audio). I'm pretty stable at around 23ms latency on my POS laptop.

---

### Post by RadicalRebel on 2012-03-12
Thanks a bundle! I ll check kxstudio out for sure. I know Audacity's 1.3 BETA is decent for open source editing. I have a few other audio programs, just wanted to try messing around Linux alternatives because feeware is so great.

 I was thinking of to start messing around with Blender as well for video creation or even working towards game development in the future. Can I get Blender on it's own or with another Ubuntu download? I have tryed a bit of flash but mostly stick pivot animator[lol]. As far as video creation freeware anyone have suggestions?

---

### Post by grahammechanical on 2012-03-13
I am not using Ubuntu Studio just Ubuntu and I can tell you that blender is in the Ubuntu Software Centre. These versions might install with certain sets of programs and that is useful but they are all available in the Ubuntu Software Centre in whatever Ubuntu we are using.

When you install Ubuntu, whatever version you do install, do not forget to run Additional Drivers. You may get an icon appear in the top panel. You will need to install a proprietary driver. This is especially necessary for using the Blender. I think that Blender needs to use the full OpenGL capabilities of the graphic adapter.

Regards.

---

