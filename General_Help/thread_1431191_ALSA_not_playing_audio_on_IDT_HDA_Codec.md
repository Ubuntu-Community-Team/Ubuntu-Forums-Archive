---
title: "ALSA not playing audio on IDT HDA Codec"
date: 2010-03-16
forum: General Help
---

### Post by naren2047 on 2010-03-16
Hello,
I have an issue that I have been trying to fix for the last one week and failing. 
 
I am working on an IP phone where I have two Audio codecs - 
CARD 0: IDT HDA Code for the Handset
CARD 1: NXP USB Codec for the Speakerphone
 
I can play music on each of them using command line commands. But when I use ALSA APIs, I can only play music on CARD 1 (Speaker phone) and not on CARD 0 at all.
 
The code I have for CARD 1 is:
snd_pcm_open(&phandle, "plughw:1,0", SND_PCM_STREAM_PLAYBACK, 0);
 
I have all the other API calls as well.. and I am using PCM STREAM RATE = 16000, Channels = 1 for initializing.
 
THIS WORKS GREAT!
 
BUt when I change the devide to: "plughw:0,0" -- I get no audio on the handset.
 
Can someone please help me resolve this issue... what could be the problem?
 
Thanks
Naren

---

### Post by jcbrown on 2010-04-20
> **naren2047 said:**
> Hello,
I have an issue that I have been trying to fix for the last one week and failing. 
 
I am working on an IP phone where I have two Audio codecs - 
CARD 0: IDT HDA Code for the Handset
CARD 1: NXP USB Codec for the Speakerphone
 
I can play music on each of them using command line commands. But when I use ALSA APIs, I can only play music on CARD 1 (Speaker phone) and not on CARD 0 at all.
 
The code I have for CARD 1 is:
snd_pcm_open(&phandle, "plughw:1,0", SND_PCM_STREAM_PLAYBACK, 0);
 
I have all the other API calls as well.. and I am using PCM STREAM RATE = 16000, Channels = 1 for initializing.
 
THIS WORKS GREAT!
 
BUt when I change the devide to: "plughw:0,0" -- I get no audio on the handset.
 
Can someone please help me resolve this issue... what could be the problem?
 
Thanks
Naren[FONT=Calibri][SIZE=3]This isn’t easy as one might  expect. The two codec’s that you have listed here seems to be audio.  The problem here is that you can only play music on card 1 and not card  0 when ALSA API’s, right? Well, I say you wait for someone to solve  this![/SIZE][/FONT]

---

