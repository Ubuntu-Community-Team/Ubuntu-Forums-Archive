---
title: "http://localhost:54044. The site says: &quot;administrator&quot;"
date: 2009-10-24
forum: General Help
---

### Post by Merovius on 2009-10-24
After a hell of a morning getting Windows 7 set up on my sons gaming pc and resetting the whole home network and knocking out the internet conection to the whole house (#@$$!%% Windows) I now get this password field popping up every time I start Firefox.

A username and password are being requested by [http://localhost:54044](http://localhost:54044). The site says: "administrator"

With a user name and password field. 

What the heck is this? Does his machine already have malware on it that is trying to get through to mine or something?

:mad:

TIA

---

### Post by Wim Sturkenboom on 2009-10-24
Is your problem in Ubuntu or in Windows? Did you do a bit of google on localhost:54044 to check if one of the hits might apply?

---

### Post by Merovius on 2009-10-24
I am getting this password request under Ubuntu 9.10.

I did a Google search and got almost no hits. I changed it around a bit and got one German site I can't read.

It does not appear to effect Google Chrome. Only Firefox.

TIA

---

### Post by DeMus on 2009-10-24
> **Merovius said:**
>  I changed it around a bit and got one German site I can't read.

What is the address of the German site? I can take a look for you.

---

### Post by 101011010010 on 2009-10-24
Hello there,
I know this sounds funny, but it sounds like your home page has been set to that address. Try edit> preferences>main, and try changing it.
I hope this helps.

---

### Post by Merovius on 2009-10-24
[www.hijackthis-forum.de/archiv/29139-ie-popups-trotz-firefox.html](www.hijackthis-forum.de/archiv/29139-ie-popups-trotz-firefox.html)

Thanks :)

---

### Post by SPr on 2009-10-24
```

sudo netstat --tcp --udp --listening --program --numeric

```
Post the output of that command and it should say what is listening on that port.

---

### Post by diesch on 2009-10-24
What do you get if you run
  ```
sudo fuser -v 54044/tcp
```in a Terminal?

---

### Post by Merovius on 2009-10-24
Restored default home / start page and it still wants a username / password..

---

### Post by Merovius on 2009-10-24
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:36564         0.0.0.0:*               LISTEN      2740/ssl_esock  
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN      1723/cupsd      
tcp        0      0 127.0.0.1:54044         0.0.0.0:*               LISTEN      2519/beam       
tcp6       0      0 :::2500                 :::*                    LISTEN      1533/inetutils-inet
tcp6       0      0 :::139                  :::*                    LISTEN      1597/smbd       
tcp6       0      0 :::60813                :::*                    LISTEN      2234/apache2    
tcp6       0      0 :::631                  :::*                    LISTEN      1723/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      1597/smbd       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1129/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1083/avahi-daemon: 
udp        0      0 0.0.0.0:41329           0.0.0.0:*                           1083/avahi-daemon: 
udp        0      0 0.0.0.0:631             0.0.0.0:*                           1723/cupsd      
udp        0      0 192.168.0.3:137         0.0.0.0:*                           1575/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1575/nmbd       
udp        0      0 192.168.0.3:138         0.0.0.0:*                           1575/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1575/nmbd

---

### Post by Merovius on 2009-10-24
steve@steve-desktop:~$ sudo fuser -v 54044/tcp
                     USER        PID ACCESS COMMAND
54044/tcp:           steve      2519 F.... beam

---

### Post by diesch on 2009-10-24
> **Merovius said:**
> [www.hijackthis-forum.de/archiv/29139-ie-popups-trotz-firefox.html]("http://www.hijackthis-forum.de/archiv/29139-ie-popups-trotz-firefox.html")


It's about cleaning a Windows installation that has several trojans installed.

---

### Post by Merovius on 2009-10-24
Did I mention I'm becoming a Windows hater...

I installed the antivirus / malware software that Microsoft is giving away these days. Maybe I should yank it and put AVG back on there and Zone Alarm as he had with XP.

No problems then.. During the install he was without both for about 5 minutes. What are the chances he got hit during that time? I guess it could have been carried over in something he backed up.

---

### Post by SPr on 2009-10-24
> **Merovius said:**
> ...    
tcp        0      0 127.0.0.1:54044         0.0.0.0:*               LISTEN      2519/beam      
> **Merovius said:**
> 
54044/tcp:           steve      2519 F.... beam
Do you have any idea what the program "beam" could be? It is installed on the Ubuntu PC (127.0.0.1 = the computer the commands were run on).

I've searched Google and the Debian repos and not found anything.

---

### Post by diesch on 2009-10-24
> **Merovius said:**
> steve@steve-desktop:~$ sudo fuser -v 54044/tcp
                     USER        PID ACCESS COMMAND
54044/tcp:           steve      2519 F.... beam

So it's a program called "beam" running as user "steve".

What does
 ```
ps -p      2519 -ocmd
```
print?

---

### Post by Merovius on 2009-10-24
Never heard of it..

I have UbuntuOne, Gwibber, CheckGmail

No clue.

---

### Post by Merovius on 2009-10-24
steve@steve-desktop:~$ ps -p      2519 -ocmd
CMD
/usr/lib/erlang/erts-5.7.2/bin/beam -Bd -K true -- -root /usr/lib/erlang -progna

---

### Post by diesch on 2009-10-24
So it's something related to the [Erlang](http://www.erlang.org/) virtual machine (package erlang-base or erlang-base-hipe). If you don't use Erlang try to remove this packages and see if that will remove anything you want.

---

### Post by Merovius on 2009-10-24
A synaptic search shows it has something to do with CouchDB and therefore it's connected to UbuntuOne and Evolution / FIREFOX synching.

Thanks now I have a pretty good idea whats going on. I think I need to figure out what username password it want's or wait for more UbuntuOne updates.

Their updates have been raising heck lately..

Thanks again All. I will post again if I get it figured out completely.

---

### Post by DeMus on 2009-10-24
> **Merovius said:**
> [www.hijackthis-forum.de/archiv/29139-ie-popups-trotz-firefox.html](www.hijackthis-forum.de/archiv/29139-ie-popups-trotz-firefox.html)

Thanks :)

Well this German site is about popups, viruses and other malware on Windows computers and how to get rid of them.
Not what you are looking for , is it?

---

### Post by Merovius on 2009-10-24
Probably not at this point. Think it's UbuntuOne.

Thanks for taking the time to read it though. Got to love the forums..:)

---

### Post by Merovius on 2009-10-25
Well, I was right about the connection to CouchDB etc. I uninstalled "bindwood" which has to do with syncing Firefox bookmarks and the login requests have stopped. Not sure how bindwood got installed to begin with. Might have done it myself.

At least it has stopped.

---

