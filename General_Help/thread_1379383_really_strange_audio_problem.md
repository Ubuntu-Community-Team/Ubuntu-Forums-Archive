---
title: "really strange audio problem"
date: 2010-01-12
forum: General Help
---

### Post by taft-ita on 2010-01-12
hi , 
I'm facing a strange behaviour of my PC audio (card ? module ? programs ? ) , main problem is during playing sound (mp3 ,wav ,ogg ) and video (avi - youtube ecc ).

after play i hear a noise coming out mainly from right speaker , often a intermittent , sometimes ritmic noise + a base frying noize 

the really strange things is that,  if i STOP and START again the same song ( MPlayer , VLC do this , Totem , Rithmbox , don't ! ) maybe not the first time but second or third YES ! the sound is perfect , no noise at all ! 

I've checked almost everything , from changhing PCI card position to reloading , reinstalling reconfiguing alsa modules ,  improving latency until real time kernel_rt 

it seems all ok 

sound card is an old soundblaster live platinum + LiveDrive (someone knows if it can work? ) .
kernel  2.6.31-17-generic.
naturally last ubuntu release. 

some ideas what to do now ? 

thanks davide.

---

### Post by khelben1979 on 2010-01-12
Try another kernel release. Might be worth a try in my opinion.

---

### Post by taft-ita on 2010-01-12
UPDATE 

removed Pulsaudio , nothing changed except i lost rear out 


I've tested statistically when disappear the noise and saw that  
every file must be opened 3 times or 4  and then sounds good !  

I don't understand !

going back with kernel until 2.6.27-11 or stay with 2.6.31-?
thanks

---

### Post by khelben1979 on 2010-01-12
In that case, go for 2.6.27-11 or compile your own.

[Linux26changes]("http://kernelnewbies.org/Linux26Changes") (enjoy!)

---

### Post by taft-ita on 2010-01-18
update: 
 
tried  2.6.27-11 kernel , no difference , back to 2.6.31-17

upgrade ALSA :
cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Jan 18 2010 for kernel 2.6.31-17-generic (SMP).

no way . 

or soundfiles play well the first time , or i have to open it 3 times , alway 3 times ... 
now i'm guessing about codec for mp3 or access to file ...

---

### Post by 7raTEYdCql on 2010-01-18
Will Gstreamer or xine make a difference. Don't think so, but take a shot at it.

---

### Post by taft-ita on 2010-01-20
hi , 
for gstreamer i only have these commands , but also the test in gstreamer-properties make the same joke ! 
first time ... bad sound
second time - bad sound
third time ... good sound :-)

gstreamer-codec-install  
gstreamer-properties 

any other gstreamer commands ?

i don'y have xine installed at the moment , i'll try ...

---

