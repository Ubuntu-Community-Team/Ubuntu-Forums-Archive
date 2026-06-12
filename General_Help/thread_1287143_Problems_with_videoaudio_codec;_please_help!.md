---
title: "Problems with video/audio codec; please help!"
date: 2009-10-09
forum: General Help
---

### Post by viking_maniac on 2009-10-09
Me and my friends do very often send videos taken with our cellphones to each other and send them via e-mail. On Windows Vista I used software with my cellphone to watch them on my computer, like my friends do, but this software doesn't support Linux. I tried VLC and MPlayer for Linux to watch them; both manage to show the video, but none are able to give me any audio. :(

We all got Nokia cellphones with .3gp video format.

I'm really hoping that there's a codec or player (preferably in the package manager) that can solve this problem; or a converter that can read both video and audio and convert to a more default format? Or does anyone have any other suggestions to this problem?

Thanks in advance!

---

### Post by Chronon on 2009-10-09
Try this: [http://ubuntuforums.org/showthread.php?t=363073](http://ubuntuforums.org/showthread.php?t=363073)

---

### Post by andrew.46 on 2009-10-10
Hi viking,

> **viking_maniac said:**
> We all got Nokia cellphones with .3gp video format.

I'm really hoping that there's a codec or player (preferably in the package manager) that can solve this problem

It could very well be that these 3gp files contain amr sound. Under Jaunty the easiest way to play this back is by using the MPlayer available in [Medibuntu]("https://help.ubuntu.com/community/Medibuntu").

All the best,

Andrew

---

### Post by viking_maniac on 2009-10-10
> **andrew.46 said:**
> Hi viking,
 It could very well be that these 3gp files contain amr sound. Under Jaunty the easiest way to play this back is by using the MPlayer available in [Medibuntu]("https://help.ubuntu.com/community/Medibuntu").


This actually worked! Though this version of mplayer didn't play the cell files very smooth, but it works and I have sound now.

Thanks!

---

### Post by andrew.46 on 2009-10-10
Hi viking,

> **viking_maniac said:**
> This actually worked! Though this version of mplayer didn't play the cell files very smooth, but it works and I have sound now.

Great news! The bad news is that under Karmic Koala Medibuntu will not be providing a copy of MPlayer and so far the repository MPlayer does *not* feature support for amr. Interesting times ahead :).

Andrew

---

### Post by SuperSonic4 on 2009-10-10
Does medibuntu's VLC have it?

I hate amr sound with a passion but that's beyond the point lol

---

### Post by andrew.46 on 2009-10-10
Hi SuperSonic,

> **SuperSonic4 said:**
> Does medibuntu's VLC have it?

I don't believe that Medibuntu actually *has* a package for vlc although I have been wrong before :). It is not such a huge matter for vlc to playback amr files as it uses FFmpeg's libavcodec for this purpose. However the repository FFmpeg does not feature support for amr at the moment so vlc does not play it :(. This will more than likely change at some stage as there is a new open implementation of amr called libopencore-amr that is supported by the svn FFmpeg.

If you compile your own it can be done though. I attach a screenshot of vlc playing [this amr file]("http://www.andrews-corner.org/samples/Rammstein_Du_Hast.3gp") quite successfully. 

> I hate amr sound with a passion but that's beyond the point lol

Indeed the sound is pretty bad :).

Andrew

---

### Post by SuperSonic4 on 2009-10-11
> **andrew.46 said:**
> Hi SuperSonic,



I don't believe that Medibuntu actually *has* a package for vlc although I have been wrong before :). It is not such a huge matter for vlc to playback amr files as it uses FFmpeg's libavcodec for this purpose. However the repository FFmpeg does not feature support for amr at the moment so vlc does not play it :(. This will more than likely change at some stage as there is a new open implementation of amr called libopencore-amr that is supported by the svn FFmpeg.

If you compile your own it can be done though. I attach a screenshot of vlc playing [this amr file]("http://www.andrews-corner.org/samples/Rammstein_Du_Hast.3gp") quite successfully. 



Indeed the sound is pretty bad :).

Andrew

Fair enough, I just remember PLF mandriva having one and since PLF and Medibuntu do much the same thing I thought there may be one. Here's hoping though.

Also du hast is an excellent song :D

---

### Post by viking_maniac on 2009-10-11
> **andrew.46 said:**
> 
Great news! The bad news is that under Karmic Koala Medibuntu will not be providing a copy of MPlayer and so far the repository MPlayer does *not* feature support for amr. Interesting times ahead :).


Are you sure this is permanent? Or if mplayer will eventually come to Koala?

---

### Post by viking_maniac on 2009-10-11
BTW, [B]andrew.46

[/B]Are there any other permanent solutions to just make Mplayer (or whatever player) to play arm audio?

---

### Post by viking_maniac on 2009-10-11
I don't mean to spam this thread, I just want to say that my problem is solved!

Here's what to do to be able to play .3GP files with arm sound in any Ubuntu OS (correct me if I'm wrong!):

> 1. Download latest RealPlayer (v.11) for Linux at [http://europe.real.com/realplayer/other-versions/](http://europe.real.com/realplayer/other-versions/) and save to Desktop.
2. Open Terminal:
[COLOR=Red][B][COLOR=Black][COLOR=Red]$[/COLOR] cd Desktop
[COLOR=Red]$[/COLOR] sudo chmod a+x RealPlayer11GOLD.bin
[COLOR=Red] $[/COLOR] sudo ./RealPlayer11GOLD.bin[/COLOR][/B]
[/COLOR]3. Follow install instructions in Terminal
4. Done! You'll now find RealPlayer 11 in Applications -> Sound & VideoThey all (.3GP/arm) play flawlessly with sound now! :D

---

### Post by andrew.46 on 2009-10-12
Hi viking,

> **viking_maniac said:**
> ]Are there any other permanent solutions to just make Mplayer (or whatever player) to play arm audio?

I run a series of guides on these forums that build a copy of MPlayer capable of amr playback. I am testing one for Karmic at the moment:

[http://ubuntuforums.org/showthread.php?t=1280543](http://ubuntuforums.org/showthread.php?t=1280543)

Life is a bit easier on Karmic as the relevant libopencore-amr libraries are held in the repository.

Andrew

---

