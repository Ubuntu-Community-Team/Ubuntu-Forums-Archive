---
title: "Trying to record a google voice (through gmail) call"
date: 2012-10-08
forum: General Help
---

### Post by Jmob on 2012-10-08
Title says it all, (other than that I'm in a 1-party consent state so there are no legal issues here), just trying to figure out how to do this.  

I can get audacity to read the call output, or I can get it to read the mic, but I haven't figured out how to get both (presumably by directing both the through the main output, though if there's another way, I'm open to it.)

Sorry if I'm not bringing a lot to the table here, but I'm flying blind a bit.  Anyone have some direction?

---

### Post by HiImTye on 2012-10-09
if you're using PulseAudio, just use pavucontrol and set whatever you are using to record to 'monitor of *device*' in the 'Recording' tab

---

### Post by Habitual on 2012-10-09
simple sox+bash script  will record whatever comes out of the speakers. 
I've heard that /dev/dsp is no longer being used in the recent Ubuntu OS to which I cannot speak, 

Hope it may help...

                                    [Record what comes out of your speakers]("http://www.bournetoraiseshell.com/article.php/20101116231547304?query=sox")

---

