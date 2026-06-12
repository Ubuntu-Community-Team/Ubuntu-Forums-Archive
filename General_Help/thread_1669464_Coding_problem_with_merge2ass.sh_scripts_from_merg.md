---
title: "Coding problem with merge2ass.sh scripts from merging two subtitles"
date: 2011-01-17
forum: General Help
---

### Post by Eng.AbuWleeD on 2011-01-17
Hi , Guys there is a script named merge2ass.sh and this is the link :
[ftp://ftp.berlios.de/pub/smplayer/tools/merge2ass.sh](ftp://ftp.berlios.de/pub/smplayer/tools/merge2ass.sh)
this script for merge 2 subtitles in one new subtitle file. and when play the movie you will see 2 subtitles 
one above screen and one below .so you can set tow languages .
so this script works fine for me but when I set Arabic one of the tow languages the process will work fine but when film show the Arabic language will appear like question marks (????)
I am sure the problem not from the player because it is also appears as question marks in the generated file(result from two subtitles merging).
I think the problem is the coding. I have to make some configuration special for the Arabic language.
there is a link in Smplayer forums that talke about this scripts and how to use it.
[http://smplayer.berlios.de/forums/viewtopic.php?id=1487](http://smplayer.berlios.de/forums/viewtopic.php?id=1487)
please any suggestions to the way that I can solve my problem.
Thanx in advance.

Best Regards
Bilal Salas

---

### Post by Eng.AbuWleeD on 2011-01-19
guys any question about my thread??
any missed information in my first post?
help me.this forum for human-being and I am a human.
so please help me.
Thanx alot

---

### Post by jose1711 on 2011-02-24
try inserting -utf8 in front of -dumpsrtsub in the script

---

### Post by hefaistos2001 on 2011-04-20
> **jose1711 said:**
> try inserting -utf8 in front of -dumpsrtsub in the script

Thanks jose1711, that worked for me! And also thanks for the script :)

---

### Post by swans100 on 2011-05-25
Hi! 

-unicode instead -utf8 worked better for me.

BTW, I found a **problem with SRT subtitles using milliseconds precision**. SSA format does not support millisecond, and players go crazy if you use them. Therefore, the script should remove them.

Here are the necessary changes. Change the function generate_ssa_dialogs() for the following one:

```
generate_ssa_dialogs(){
sed -e "/ --> /s/,/./g" "${sub[1]}-temp" | tr -d "\r" | awk 'BEGIN{ORS="";print " "} / --> /,/^$/ {ORS=" ";print} /^$/{print "\n"}' | sed -e "s/ --> /,/g" -e "s/^ \([^ ]*\) \(.*\)/Dialogue: Marked=0,\1,lang1style,Cher,0000,0000,0000,,\2/" -e "s/,00:/,0:/g" -e "s/\([:,]\)0\([0-9]\)/\1\2/g" -e "s/\([0-9]\)\(.\)\([0-9]\)\([0-9]\)0\(,\)/\1\2\3\4\5/g" >>"$output"
sed -e "/ --> /s/,/./g" "${sub[2]}-temp" | tr -d "\r" | awk 'BEGIN{ORS="";print " "} / --> /,/^$/ {ORS=" ";print} /^$/{print "\n"}' | sed -e "s/ --> /,/g" -e "s/^ \([^ ]*\) \(.*\)/Dialogue: Marked=0,\1,lang2style,Cher,0000,0000,0000,,\2/" -e "s/,00:/,0:/g" -e "s/^ *//g" -e "s/\([:,]\)0\([0-9]\)/\1\2/g" -e "s/\([0-9]\)\(.\)\([0-9]\)\([0-9]\)0\(,\)/\1\2\3\4\5/g" >>"$output"
}
```Thanks for that awesome script!

---

### Post by tongo on 2013-03-31
this script not works for me!!

---

### Post by jose1711 on 2013-03-31
> **tongo said:**
> this script not works for me!!

if you want someone to help you, you'll need to give us a bit more details..

---

### Post by oldos2er on 2013-03-31
[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---

