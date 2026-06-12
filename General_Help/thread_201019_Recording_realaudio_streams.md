---
title: "Recording realaudio streams"
date: 2006-06-21
forum: General Help
---

### Post by Dafydd on 2006-06-21
Hi, 
I'm just recording a realaudio stream (bbc) thanks to k4p0w3r's instructions.

But one little question: is it possible to record straight to mp3 or do I have to convert the file from wav to mp3?
cheers

dafydd

[QUOTE=k4p0w3r]I listen alot to swedish radio because every friday at 8pm they have live broadcast with various artists. SR (swedish radio) only broadcast in Real audio. Here's how I solved it:

How to record a live-stream from Realplay or similar program.

Simple explanation:
Vsound can capture sound from any application that uses OSS /dev/dsp sound device. It basicly acts as a virtual cable between your computers "sound out" and redirects it to "line in". The sound can be saved to a wav file (using sox - automaticly).
More info can be found here:  [http://flatline.org.uk/vsound/](http://flatline.org.uk/vsound/)


1.	Install vsound
1.1	command for debian based systems: apt-get install vsound
1.2	note: vsound may require sox

2. 	Run vsound with these arguments:
2.1	command: vsound -f myrecording.wav -d soundapplication soundstream
2.2	example: vsound -f p3hiphoplive.wav -d /opt/RealPlayer/realplay rtsp://sr-rm.qbrick.com/broadcast/cluster/encoder/02038_p3.rm
2.3	note: -f outputs to the file mentioned. -d make sure you can listen to the sound at the same time it is recorded. Some applications like RealPlayer need this to work.

After the recording is made (file will be written after you close the Realplayer) just convert the wav to ogg or mp3  \\:D/[/QUOTE]

---

### Post by Dafydd on 2006-06-21
just recorded a stream and no have a vsound.au file. But somehow there's no wav file to convert. Using another Soundconverter program to convert but it's very sloooooow.

Also vsound needs root privileges. Don't know how to change that.

---

### Post by Dafydd on 2006-06-21
[QUOTE=Dafydd]just recorded a stream and no have a vsound.au file. But somehow there's no wav file to convert. Using another Soundconverter program to convert but it's very sloooooow.

Also vsound needs root privileges. Don't know how to change that.[/QUOTE]

Sound conversion took 10 minutes 11 seconds for a 400 MB 'au' file to a 22MB mp3 file...

---

### Post by Dafydd on 2006-06-22
[QUOTE=Dafydd]Also vsound needs root privileges. Don't know how to change that.[/QUOTE]

Don't know if this is the best way but I uninstalled vsound with synaptic, downloaded a vsound deb package and then did: sudo dpkg -i vsound....deb

now I can use vsound as a normal user.

it's a great program for recording realaudio streams for your mp3 player

---

### Post by Dafydd on 2006-06-22
[QUOTE=Dafydd]Sound conversion took 10 minutes 11 seconds for a 400 MB 'au' file to a 22MB mp3 file...[/QUOTE]

I did 

lame -f /home/dafydd/Desktop/vsound.au /home/dafydd/Desktop/vsound.mp3

and the conversion was done in around 2 minutes for a 800MB au file.

---

