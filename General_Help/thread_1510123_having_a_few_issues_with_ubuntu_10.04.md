---
title: "having a few issues with ubuntu 10.04"
date: 2010-06-15
forum: General Help
---

### Post by jimmythy on 2010-06-15
hi, im new to this unix based operating system business but here goes

i recently installed ubuntu 10.04 on my computer, im finding it quite enjoyable, however i am having a few different problems. here they are:

slow copys from and to my external harddrive, i get no speeds faster the 1mb/s, i googled this problem and found a few different ways to solve the problem, the main one being this [http://ubuntuforums.org/showpost.php?p=5447719&postcount=10](http://ubuntuforums.org/showpost.php?p=5447719&postcount=10) however i cannot find the menu.lst file, and im not sure if it would even work for 10.04

my other main issues revolve around Amarok, i get lag when i press the play/pause button, a good few seconds of it, ive googled that as well, with nothing i can understand. i also seem to get the same lag when a song ends, with the first few seconds of the next song being cut off sometimes.

i also get the error message "the audio plaback device HDA Intel (ALC889A) does not work falling back to playback/recording through pulseaudio server" i don't know whether or not these to issues are related.

if anyone can shed some light it would be great, thanks

---

### Post by mikewhatever on 2010-06-15
1. To apply that fix in 10.04, you'll need to edit /etc/default/grub file.
```
gksudo gedit /etc/default/grub
```
now, find the following line and add *pci=routeirq* to it
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
so that it looks like this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=routeirq"
```
then save and exit, and run the following command:
```
sudo update-grub
```
The change will take effect after rebooting. Hope it works.

2. Do you use Kubuntu or just like Amarok?  Do other players hang too?

3. When do you get the message? Do you do anything specific when it shows?

---

### Post by jimmythy on 2010-06-15
thanks very much for that fix, i'll try it shortly. 

im not using kubuntu i just like amarok, no other players have this issue with the lag just amarok.

i only get that error message when i start amarok. it happens everytime i open it.

thanks again

EDIT: just tried that fix, it didnt work. i do have several hard drives mount at startup, could this be causing the slow speeds?

---

### Post by mikewhatever on 2010-06-15
> **jimmythy said:**
> thanks very much for that fix, i'll try it shortly. 

im not using kubuntu i just like amarok, no other players have this issue with the lag just amarok.

i only get that error message when i start amarok. it happens everytime i open it.

Try loking through Amarock's audio settings, perhaps there are some clues. In case the 'pulseaudio' option is not the default, try switching to it.

> 
EDIT: just tried that fix, it didnt work. i do have several hard drives mount at startup, could this be causing the slow speeds?

Could be. Try disconnecting all but one.

---

### Post by jimmythy on 2010-06-15
i've resolved the issue with the slow transfer speeds, by changing the way i was mounting my other hard drives at startup


by moving pulseaudio up in the list of preferred audio devices it does get rid of that error message when i run amarok, however the play pause lag is still there

---

### Post by murderslastcrow on 2010-06-20
I'm having the same issue with Amarok, and I was also having the error but figured to prefer pulseaudio already. After looking through the options, it doesn't seem like there's a timer telling it to stop.

The odd thing is that clicking to go to the next or previous song is instantaneous, but when you click the pause button it takes about a second to actually stop the music, and then the pause button takes another two seconds or so to turn back into a play button so you can click it to play.

It also takes just as long if you press the spacebar instead of clicking the button, so it seems to either be a setting or some issue with Amarok 2.3. :\ I really, really like Amarok so it's kind of a pain.

Also, a similar delay occurs when clicking pause or play in the Now Playing plasmoid, so it seems to be an issue with the code. Again, I could be wrong, but this is the most relevant forum post I've found for this issue.

---

