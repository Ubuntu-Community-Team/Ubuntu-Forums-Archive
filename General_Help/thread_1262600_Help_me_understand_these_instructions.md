---
title: "Help me understand these instructions"
date: 2009-09-10
forum: General Help
---

### Post by Mad dog on 2009-09-10
I'm trying to use a program called Packet Tracer by Cisco. The Ubuntu version they gave me looks horrible, but this guy says he fixed the problem, but I can't figure out how to do what he says:

  > Unfortunately the linux version of PacketTracer looks very ugly since the fonts  are not antialiased. Today I found out how to make the fonts in PacketTracer antialiased: 

PacketTracer uses it's own bundled QT 4 library that sits in  

/usr/local/PacketTracer5/lib 

you can fix the ugly font problem by forcing packetracer to use the ubuntu QT4 version (aptitude install libqt4-gui) by commenting out the  LD_LIBARY_PATH export in line 6 of the PacketTracer startscript  /usr/local/PacketTracer51/packettracer: 

# export LD_LIBRARY_PATH=$PTDIR/lib 

 Afterwards you can remove /usr/local/PacketTracer5/lib which will free up 15M of disk space. 

Happy tracing!

Can you help me please?

---

### Post by zvacet on 2009-09-10
Type in terminal

```
cd /usr/local/PacketTracer51/packettracer
```

and then find line 6 and make it look like this

```
# export LD_LIBRARY_PATH=$PTDIR/lib
```

Save and close file.That should do it.

---

### Post by nothingspecial on 2009-09-10
```
sudo apt-get install libqt4-gui
```

```
sudo nano /usr/local/PacketTracer5/lib 
```

Then find the line that says


```
 export LD_LIBRARY_PATH=$PTDIR/lib 
```

(line 6?)

and put a # infront of it so it now says


```
# export LD_LIBRARY_PATH=$PTDIR/lib 
```

---

### Post by Jefferythewind on 2009-09-10
First, do you have the directory:

/usr/local/PacketTracer5/lib 

On your hard drive?


If you do, then you should be all set, and just do what the instructions say.

Run: ```
aptitude install libqt4-gui
```  in a terminal

Then, open this file: /usr/local/PacketTracer51/packettracer,  and put a # symbol in front of the sixth line, ie that line should look like this:

# export LD_LIBRARY_PATH=$PTDIR/lib 

then after you can remove that other library directory in your instructions.

Understand?

---

### Post by Mad dog on 2009-09-10
Thanks for your help... I installed qt4 easily enough, but the other thing is still confusing me. I can't seem to find the /usr/local/PacketTracer5 folder anywhere? I have a Packet Tracer 5 folder in my home folder but it doesn't have anything in it.

---

### Post by Mad dog on 2009-09-10
When I do this:

```
sudo nano /usr/local/PacketTracer5/lib
```

I get a blank page that I can type in.

---

### Post by nothingspecial on 2009-09-10
That`s because it doesn`t exist. If you have saved it you should probably remove it.

Do you have anything close to PacketTracer5 in /usr/lib/?

---

### Post by Mad dog on 2009-09-10
:) I didn't save it. I dont see anything like it in there. Where would all my Packet Tracer stuff be?

---

### Post by nothingspecial on 2009-09-10
```
whereis PacketTracer5
```

---

### Post by Mad dog on 2009-09-10
output:

/usr/local/PacketTracer5

---

### Post by knepig91 on 2009-09-10
Go to terminal: locate PacketTracer5

---

### Post by nothingspecial on 2009-09-10
```
ls /usr/local/PacketTracer5
```

Will tell you what`s in it

---

### Post by Mad dog on 2009-09-10
Holy crap! I didn't know usr was a folder in the Filesystem! I found it...now I have to try and figure out this crap.

---

### Post by Mad dog on 2009-09-10
So I found the /usr/local/PacketTracer5/lib  It's full of 36 files of an unknown type.

---

### Post by nothingspecial on 2009-09-10
See, if I read posts properly in the first place this wouldn`t take an hour
```

sudo nano /usr/local/PacketTracer51/packettracer
```

---

### Post by Mad dog on 2009-09-10
I DID IT:guitar: Yes! Thanks so much guys! I learned a lot. Now I can really do well in my class since I have a good Packet Tracer to use at home. Thanks again. I love how I've encountered about 20 problems since I started using Ubuntu, and they've all been 100% self servicable (with help). :P

---

### Post by Mad dog on 2009-09-10
```
sudo nano /usr/local/PacketTracer51/packettracer
```

Wow... this would have worked an hour ago... had we just left off the "1" so it should have read:

```
sudo nano /usr/local/PacketTracer5/packettracer
```

See, because I tried that and it opened right up, but when I put the (1) on there it was creating a new file.

---

### Post by nothingspecial on 2009-09-10
That`s why it`s a good idea to ask for conformation if you are not sure what a command will do before you excecute it.

---

### Post by robertrose6 on 2009-12-03
> **nothingspecial said:**
> ```
sudo apt-get install libqt4-gui
``````
sudo nano /usr/local/PacketTracer5/lib 
```Then find the line that says


```
 export LD_LIBRARY_PATH=$PTDIR/lib 
```(line 6?)

and put a # infront of it so it now says


```
# export LD_LIBRARY_PATH=$PTDIR/lib 
```



SO I have done the above and after I change line 6 to 

# export LD_LIBRARY_PATH=$PTDIR/lib  

Packettracer will not start. Am I missing something?

---

