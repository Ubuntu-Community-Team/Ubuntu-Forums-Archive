---
title: "Multiple Commands at the Terminal"
date: 2010-01-21
forum: General Help
---

### Post by skwon11 on 2010-01-21
Sorry for the the poor description/cry out for help that is coming... I just don't know the right terms to use.

I am in the process of coverting some video files to motion jpeg (Wii) files with ffmpeg (great program by the way).  I have been successful and so the majority of my work is over.  My question is simple (I think) but complex to me so... here it goes.

Is there a way on one command line to "batch" convert 8 or 9 files together instead of one by one.  I just don't know what to put on the command line.  I took one UNIX class a long time ago and the terms pipe and such come to mind... but I forget.  Any takers?  That was I can write what I want the computer to do in the morning and just come back after work and voila... done.  Thanks to anybody who answers.

---

### Post by hemimaniac on 2010-01-21
for queing jobs like that, i have been using handbrake for *unix maybe worth a shot, im still fairly new, but i try to offer what i can

---

### Post by IcarusR on 2010-01-21
If you are using exactly the same commands on each file you could put them all in the same directory & use wild cards.. ie "*.avi" instead of listing them all by name.

---

### Post by tacutu on 2010-01-21
```
for i in *.avi;
do your_command $i;
done
```

substitute your_command with whatever you want to do to the avi files.

---

### Post by andrew.46 on 2010-01-21
Hi tacutu,

> **tacutu said:**
> 
```
for i in *.avi;
do your_command $i;
done
```


It is the most minor of nitpicks but the ';' character is not required when the for loop is written in this way. Thus the following is all that is required:

```

for i in *.avi
do 
   your_command $i
done

```

My apologies for raising such a small issue of syntax :).

Andrew

---

### Post by skwon11 on 2010-01-21
```
mencoder KIDVID1.avi -fps 23.97 -ovc lavc -lavcopts vcodec=mjpeg -oac pcm -vf scale -zoom -xy 512 -o KIDVID1.avi
```

Thanks for the replies.  So if I am trying to do this to KIDVID1, 2, 3, 4, 5 and 6... how does this work?  My apologies again.

---

### Post by andrew.46 on 2010-01-21
Hi skwon,

> **skwon11 said:**
> ```
mencoder KIDVID1.avi -fps 23.97 -ovc lavc -lavcopts vcodec=mjpeg -oac pcm -vf scale -zoom -xy 512 -o KIDVID1.avi
```

Thanks for the replies.  So if I am trying to do this to KIDVID1, 2, 3, 4, 5 and 6... how does this work?  My apologies again.

```

for f in *.avi
do 
mencoder "$f" -o "${f%.avi}_converted.avi" \
         -fps 23.97 -ovc lavc -lavcopts vcodec=mjpeg \
         -oac pcm -vf scale -zoom -xy 512 
done

```

This might provide a start perhaps?

Andrew

---

