---
title: "Can anyone PLEASE help me to achieve VLC streaming?"
date: 2011-06-14
forum: General Help
---

### Post by macey on 2011-06-14
Reposting in General Help as no luck in Multimedia & Video forum.

According to this:- [http://paul-sanders.info/?p=50](http://paul-sanders.info/?p=50)

The following should work:-

vlc -vvv ~/Music/my_test_file.mp3 --sout '#transcode{acodec=mp3,ab=64,channels=2}:std{acces s=mmsh,mux=asfh,dst=8080}'

But it doesn't work. Looking at the VLC 'Media Information > Statistics' I can see the 'Audio Decoded' and 'Input read' counts increasing but the
'Output written' counts stubbornly remain at zero.
All ports on PC firewall and router have been set up correctly.

I would dearly LOVE to get vlc streaming working. I have looked through the documentation and found it little help for me. The videolan forum is most unhelpful. The typical reply is of the "read the documentation dumbo" nature.
Here's hoping the Ubuntu forum will be more friendly & helpful.
Obviously, I can post the vlc log if requested.

Running Ubuntu 11.04



Quote:
Originally Posted by nothingspecial View Post
Try specifying your ip address aswell as port. ie

Code:

dst=<ipaddress>:8080

According to that website, you can omit ipaddress. What if I want it available at any address? The writer of the article says he has used this method to broadcast to 200+ users at the same time. Did not code ip addresses. By the way, before you ask, I have tried to contact author (paul Sanders).
Thanks anyway!
Thanks in anticipation

---

### Post by nothingspecial on 2011-06-14
Not the ipaddress of the destination, but of the machine doing the streaming.

First screenshot,  right hand terminal is sshed  into my server and I've strarted streaming. The left hand terminal is the local machine playing the stream.

[ATTACH]195075[/ATTACH]

Second screenshot is my netbook playing the same stream at the same time.

[ATTACH]195076[/ATTACH]

---

### Post by nothingspecial on 2011-06-14
Sorry, you can't see that very well, but in the server I used

```
fapg --format=pls --output=./playlist.pls . && cvlc playlist.pls --sout '#standard{access=http,mux=ogg,dst=192.168.1.11:8080}'
```

Don't worry about the first bit, before the &&, it generates a playlist in the directory you are in so that vlc will play it in the correct order.

On the other 2 machines, I used

```
cvlc http://192.168.1.11:8080
```

---

### Post by macey on 2011-06-14
> **nothingspecial said:**
> Sorry, you can't see that very well, but in the server I used

```
fapg --format=pls --output=./playlist.pls . && cvlc playlist.pls --sout '#standard{access=http,mux=ogg,dst=192.168.1.11:8080}'
```

Don't worry about the first bit, before the &&, it generates a playlist in the directory you are in so that vlc will play it in the correct order.

On the other 2 machines, I used

```
cvlc http://192.168.1.11:8080
```

Thanks for the reply. I have now got it working. 
I am using 

vlc -vvv ~/Desktop/channels.conf --sout '#transcode{vcodec=DIV3,vb=3096,scale=0.75,acodec=mp3,ab=64,channels=2}:std{access=mmsh,mux=asfh,dst=:8080}'

to stream live tv from my laptop tuner. You do not need to use the server ip address in the stream command. 

To play remotely, I use :- vlc mmsh://{my_server_address}:8080

Works fine.

---

