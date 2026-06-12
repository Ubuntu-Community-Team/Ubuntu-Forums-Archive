---
title: "Voice Chat Over SSH"
date: 2009-08-16
forum: General Help
---

### Post by Psycho.mario on 2009-08-16
Is it possible to have a voice chat over ssh?

Me and my friend both have ubuntu installed he can log into my box via ssh. We both have microphones and speakers/headphones. Is there any way we can chat using ssh? Please don't say anything like Yahoo or MSN, i want something that i can use without various other programs. I also believe that msn on linux is not able to do voice chat yet.

Thanks

---

### Post by Psycho.mario on 2009-08-16
Please don't let this get buried!!

---

### Post by hibliss on 2009-08-16
Skype?

How about an open source version? Ekiga -- [http://ekiga.org/]("http://ekiga.org/")

---

### Post by ubuntwhat on 2009-08-16
SSH is just using text in the terminal, as you know, so without running another program in the GUI you would not be able to voice chat with SSH, as it doesnt have anything to natively support it.

---

### Post by HermanAB on 2009-08-16
Sorta kinda...

If you would set up two SSH tunnels with Netcat, one from your machine to hers and one from hers to yours, then you could pipe audio from your mic to her speaker and from her mic to your speaker.

You may get some ideas here: [http://aeronetworks.ca/ogg2mp3-howto.html](http://aeronetworks.ca/ogg2mp3-howto.html)

You would get better results if you toss sox into the mix as well to compand the audio and the result will be something like Skype.

You got me mildly amused with this, so if you want we can collaborate a little to get it to work - maybe call it sshkype...  

Send me a private message for my email address.

---

### Post by MrUmunhum on 2009-08-16
> **Psycho.mario said:**
> Is it possible to have a voice chat over ssh?

Me and my friend both have ubuntu installed he can log into my box via ssh. We both have microphones and speakers/headphones. Is there any way we can chat using ssh? Please don't say anything like Yahoo or MSN, i want something that i can use without various other programs. I also believe that msn on linux is not able to do voice chat yet.

Thanks
Mario,
  Here are two options I have been working on.
[LIST]
[*]Pcom, peer to peer secure VoIP.[http://64.124.13.3/projects/Pcom/]("http://64.124.13.3/projects/Pcom/")
Requires SSL libraries. Real time. No server required.
[*]VMS - Voice Messaging System - Conference SSH manager [http://64.124.13.3/projects/VMS/]("http://64.124.13.3/projects/VMS/")
Fifo messaging system, requires SSH, sftp, etc. Message sent after the recording stops. Pesudo real time. Requires vmshub for a server.

[/LIST]
I have tested VMS on Ubuntu and Fedora, it works but still need working on the documents. Source is not clean enough to release, you'll need to trust me that there are no traps. There are none.

Please let me know if you have problems. Documentation is my weak spot.

---

### Post by Psycho.mario on 2009-08-17
Thanks for all the links, i will read them today. But firstly i have to tidy my room :S

---

### Post by Psycho.mario on 2009-08-17
Just a thought, would this work:

(Computer B mic to Computer A)
```
Computer A:
nc -l -p 1000 > /dev/<speakers>

Computer B:
cat /dev/<Microphone> > nc <IP> 1000
```
```

Computer A:
cat /dev/<Microphone> > nc <IP> 1001

Computer B:
nc -l -p 1001 > /dev/<speakers>
```

---

### Post by Psycho.mario on 2009-08-17
Ok, i can forward an mp3 to vlc locally using:
```
cat file.mp3 | vlc -
```I just need another ubuntu computer to test with. I will try later...


EDIT:
If i set up one computer to listen, and direct input to vlc -, and from the other computer, direct audio through vlc like so:

```
Computer A:
nc -l -p 1000 | vlc -

Computer B:
cat file.mp3 | nc 127.0.0.1 1000
```Does anyone know the name of the microphone? (e.g /dev/mic?)




EDIT 2:
I can pipe using ssh like so:
```
cat filename.mp3 | ssh 127.0.0.1 'mpg123 -'
```
However, i am not sure if this plays the filename.mp3 localy or remotely, i don't currently have another ubuntu box set up at the moment, i might boot up my other computer with the livecd to try it out.


I still would like to know if anyone knows the name of the microphone device in /dev?

---

