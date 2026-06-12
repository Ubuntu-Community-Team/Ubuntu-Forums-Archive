---
title: "Bash Read not triggering prompt"
date: 2011-08-31
forum: General Help
---

### Post by djbushido on 2011-08-31
Alright, music re-organization time. I'm trying to write a bash script to help me decide what songs I do and do not want to keep. The condition is that I want to hear the song while I'm deciding, to job my memory.
What I currently have is as follows:

cat music_list.txt | while read line;
do
nyxmms2 add "$line"
nyxmms2 play
read -p "Keep this song?: " input
if [ "$input" != "y" ]; then
    rm $line
fi
nyxmms2 stop
nyxmms2 clear
done

The problem being that I never see the prompt for the read. nyxmms2 performs it's operation and then returns, it is non-blocking. So why don't I see the read prompt?

EDIT: Accidentally typed an extra "done" that wasn't in the original script.

---

### Post by apmcd47 on 2011-08-31
Try changing the first line to:
[PHP]exec 3< music_list.txt
while read -u3 line[/PHP]

You are using the same file descripter for the keyboard and redirection of the file contents to the standard input. It is also a useles use of cat, but that is a different story. What I am doing here is opening the file in the same way you might in C or another programming language. The *read -u* reads from that file using the file descripter used in the *exec *command.

Andrew

---

### Post by sisco311 on 2011-08-31
EDIT: oops, apmcd47 beat me to it. :)

See: [http://mywiki.wooledge.org/BashGuide/InputAndOutput](http://mywiki.wooledge.org/BashGuide/InputAndOutput)

Both of your read commands read a line from the file.

Redirect the file to another FD (FD6) and read the file names from that FD and read your input form stdin: 

```
while read -r **-u 6** file
do
    something "$file"
    read -r whatever
    somethingelse
done **6<** filename.txt

```

---

### Post by Slim Odds on 2011-08-31
BTW.... this: ```
if [ "$input" != "y" ]; then
    rm $line
fi
```... is a very bad idea.... it means that if you mistype, you'll delete the song.

Much better to look for positive response or ask again for anything you don't expect.

---

### Post by sisco311 on 2011-08-31
> **Slim Odds said:**
> BTW.... this: ```
if [ "$input" != "y" ]; then
    rm $line
fi
```... is a very bad idea.... it means that if you mistype, you'll delete the song.

Much better to look for positive response or ask again for anything you don't expect.

moreover, rm will fail with files with spaces

@OP: Use more quotes!See: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes) and [http://wiki.bash-hackers.org/syntax/words](http://wiki.bash-hackers.org/syntax/words)

I would probably use a case statement, something like:
```
read -r "Delete $file? [y/N]" input
case "$input" in
    y|Y) echo "rm -- $file" ;;
      *) echo "keep it";;
esac
```

or simply **rm -i "$file"**.

---

### Post by djbushido on 2011-08-31
> **sisco311 said:**
> moreover, rm will fail with files with spaces

@OP: Use more quotes!See: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes) and [http://wiki.bash-hackers.org/syntax/words](http://wiki.bash-hackers.org/syntax/words)

I would probably use a case statement, something like:
```
read -r "Delete $file? [y/N]" input
case "$input" in
    y|Y) echo "rm -- $file" ;;
      *) echo "keep it";;
esac
```

or simply **rm -i "$file"**.

I was quoting plenty, I promise. I just can't type. The script was created on another computer, and the synergy clipboard buffer decided to not work on me.
Beyond that, this is being done with a backup of the music, not the actual collection just yet. I do understand what I'm getting into with the "not yes" logic, but I do appreciate the warning.
Anyway, thank you, I think I see what's been going on. Stdin is FD 1 IIRC?
By any means, thank you guys so much, I'll let you know how it goes tomorrow!

EDIT: Got it working, putting the input file on not stdin worked out just fine, thank you!

---

