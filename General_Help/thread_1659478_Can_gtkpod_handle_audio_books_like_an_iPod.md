---
title: "Can gtkpod handle audio books like an iPod?"
date: 2011-01-04
forum: General Help
---

### Post by Scunnered on 2011-01-04
I noted in another post that gtkpod was suggested for audio book use.  I had a look at the documentation but it did not give any clear indication of this.

Using iTunes it is possible to link all the tracks on 1 CD which makes for uninterupted listening and will also offer the facility to stop and re-start the book from where I left off. Is this available using gtkpod?

My laptop is purely a Linux setup. I am told that I would have to change the BIOS settings which is well beyond my capabilities. As I particularly wish to keep my system pure I need to find the best possible way to work with audio books rather than to capitulate to Microsoft or Apple.

Your assistance will be appreciated.

---

### Post by Scunnered on 2011-01-06
Bump

Who will rid me of this troublesome pair (M$ & Apple) ???

---

### Post by lrgmmc on 2011-01-06
hey have a look here. it shows how to take an audio book cd and convert it to the m4b file for the ipod.
[http://www.brighthub.com/computing/linux/articles/41095.aspx](http://www.brighthub.com/computing/linux/articles/41095.aspx)

---

### Post by Scunnered on 2011-01-06
**lrgmmc**

That looks just like what I am looking for.  Seems a bit long winded but if it works then patience will have to be a virtue

Many thanks for your reply.  Will give it a go and report back.

---

### Post by lrgmmc on 2011-01-06
and alot of that could be put into a script and then you only call that script and it will do the rest for you.

---

### Post by Scunnered on 2011-01-06
**lrgmmc**

That would be ideal except for the fact that creating a script is well beyond my capacity.  I took up Linux after retiring and whilst I am making progress there are areas that leave me scratching the wood.

I gave the instructions a try and have ended up totally confused. Having loaded all the required packages and processed the first CD I attempted to convert the files.  Accepting that I am a fully paid up idiot I took the instruction 

"lame -b 64 <input file.wav> <output file.mp3>" 

at face value only to find that that did not work.  I then went to look for the .wav files to see what they were called but the cupboard was bare.

Looking at Applications > Accessories & Sound and Video nothing, similarly there was nothing in the music folder either.

I am now up the proverbial creek and looking for someone with a large paddle to extricate me from this difficulty.

Feel free to offer me euthanasia for my birthday if this involves far too much assistance.

Yours in frustration

---

### Post by lrgmmc on 2011-01-06
in the directory of the files type ```
ls -l
``` in the terminal and i can help further.

---

### Post by Scunnered on 2011-01-07
**lrgmmc**

That was a great help !  Found the .wav files littering up the home folder.

That now poses the question of how the input file and output files are expressed.  I assume that the input is track01.cdda.wav and the output will be the same but ending .mp3. Are each of these contained within the <> brackets?

When the mp3 is changed to mp4 how is the book named?  When using iTunes I name the book as Hitchhiker's 01/05 for the first CD and 02/05 etc etc is this done in similar fashion for this method?

That code provided is magic and I have added it to my Idiots Guide for future reference.

Again my thanks for all your assistance

---

### Post by lrgmmc on 2011-01-07
ok open gedit and paste this in there. it will convert the cd for you.
```

#!/bin/bash
`cdparanoia -B`
for f in $(ls *.wav); do
     i=(`echo $f | sed -e 's/.wav/.mp3/g'`)
     `lame -b 64 $f $i`
done
`mp3wrap temp.mp3 *.mp3`
[LEFT][COLOR=#000000]`mplayer -vc null -vo null -ao pcm:nowaveheader:fast:file=temp.pcm ./temp.mp3`[/COLOR]
[COLOR=#000000][COLOR=#000000]`faac -R 44100 -B 16 -C 2 -X -w -q 80 --artist $2 --album $1 --track "1" --genre "Audiobooks" --year $3 -o $1.m4b ./temp.pcm`[/COLOR][/COLOR][/LEFT]
 
 

```
 
[LEFT][COLOR=#000000][COLOR=#000000]ok after that is all entered into gedit save it in to a new folder as audiobooker.sh[/COLOR][/COLOR][/LEFT]
 
[LEFT][COLOR=#000000][COLOR=#000000]ie: /home/somebody/audiobooks[/COLOR][/COLOR][COLOR=#000000][/LEFT]
 
[LEFT][COLOR=#000000]then open terminal and cd to that directory.[/COLOR][/LEFT]
 
[LEFT][COLOR=#000000]ie: ```
cd /home/somebody/audiobooks
```[/COLOR]

[COLOR=#000000]then make audiobooker.sh exicutible[/COLOR]
[LEFT][COLOR=#000000]ie: ```
chmod +x ./audiobooker.sh
```[/COLOR]
[COLOR=#000000]now run it with with the correct arrguments.[/COLOR]
[COLOR=#000000]ie: ```
./audiobooker.sh Hitchhiker's auther year
```[/COLOR]
[COLOR=#000000]the first arrgument is the book name second is auther and last is year. i dont have white space handling so no spaces. if you want the book title to be Hitchhiker's 1/5 do Hitchhiker's_1-5 the '/' also may cause problems. best not to use them.[/COLOR]
let me know how it goes.[/LEFT]
[/LEFT]

 
 
 
 
 
 
 
 
[/COLOR]

---

### Post by Scunnered on 2011-01-07
Again my thanks for your kind reply.

I think that I am getting the grasp of things, correct me if I am wrong.

1: The first set of code is what I would assume you referred to as **"a script"** and will do everything that were separate steps in the link that you provided.

2. "**make audiobooker.sh exicutible**"  Is this a one of instruction or is it needed each time I process a CD?

3. "**now run it with with the correct arrguments**" from the way that you have shown the instruction I read it as where I name the book.
When you advise that I should use Hitchhiker's_1-5 I am happy with that on the assumption that the next CD will be 
 Hitchhiker's_2-5 etc etc.  Would I therefore be correct in assuming that with a 12 CD book that I should number as Hitchhiker's_01-12 and follow on as before?  This then in theory should have all the CDs follow in sequence.

You have caught me out slightly as I have a prior engagement tonight and will not be able to do anything with this until tomorrow.

I will give it a try then and advise further.

Again thanks

PS: on looking at the last two codes you show ./ are these hidden files?

---

### Post by lrgmmc on 2011-01-07
1) yes this is a script.
2) no chmod only needs to be run the first time.
3) yes that naming would work just fine.
and dont forget the year. if you dont want it let me know. can remove it from the code. but at the moment it needs something there.

---

### Post by Scunnered on 2011-01-08
I followed your instructions and everything looked to be going well but on completion of the first disk an error message displayed.  I had a look at my home folder where I had originally saved your script as instructed in audiobooks and found that it contained both the audiobooker.sh folder and 14 wave files.  I had thought that your script would have joined the 14 files into one and converted them to MP4 or was I mistaken?

I decided to try another CD and entered ./audiobooker.sh Hitchhiker's_2-5 auther year 2005 to find that in the first instance on entering nothing happened. On re-entering it did react but provided an error message.

I have appended both the original error message and the subsequent one for your information.

I hope this is clear enough for you and look forward to your reply.

Again my thanks for all your assistance.

./audiobooker.sh Hitchhiker's_1-5 auther year 2005 
cdparanoia III release 10.2 (September 11, 2008) 
 
Ripping from sector       0 (track  1 [0:00.00]) 
	  to sector  304475 (track 14 [4:35.13]) 
outputting to track01.cdda.wav 
 (== PROGRESS == [                              | 019753 00 ] == :^D * ==)   
outputting to track02.cdda.wav 
 (== PROGRESS == [                              | 038361 00 ] == :^D * ==)   
outputting to track03.cdda.wav 
 (== PROGRESS == [                              | 060918 00 ] == :^D * ==)   
outputting to track04.cdda.wav 
 (== PROGRESS == [                              | 079642 00 ] == :^D * ==)   
outputting to track05.cdda.wav 
 (== PROGRESS == [                              | 089242 00 ] == :^D * ==)   
outputting to track06.cdda.wav 
 (== PROGRESS == [                              | 118101 00 ] == :^D * ==)   
outputting to track07.cdda.wav 
 (== PROGRESS == [                              | 145248 00 ] == :^D * ==)   
outputting to track08.cdda.wav 
 (== PROGRESS == [                              | 172368 00 ] == :^D * ==)   
outputting to track09.cdda.wav 
 (== PROGRESS == [                              | 192526 00 ] == :^D * ==)   
outputting to track10.cdda.wav 
 (== PROGRESS == [                              | 210002 00 ] == :^D * ==)   
outputting to track11.cdda.wav 
 (== PROGRESS == [                              | 231277 00 ] == :^D * ==)   
outputting to track12.cdda.wav 
 (== PROGRESS == [                              | 256274 00 ] == :^D * ==)   
outputting to track13.cdda.wav 
 (== PROGRESS == [                              | 283836 00 ] == :^D * ==)   
outputting to track14.cdda.wav 
 (== PROGRESS == [                              | 304475 00 ] == :^D * ==)   
Done. 

./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 5: lame: command not found 
./audiobooker.sh: line 7: mp3wrap: command not found 
./audiobooker.sh: line 8: mplayer: command not found 
./audiobooker.sh: line 9: faac: command not found 
ian@ubuntu:~/audiobooks$


Second message

 ian@ubuntu:~$ ./audiobooker.sh Hitchhiker's_2-5 auther year 2005
> ./audiobooker.sh Hitchhiker's_2-5 auther year 2005
bash: ./audiobooker.sh: No such file or directory
ian@ubuntu:~$

PS is there an easy way to work with the terminal to let me change the book name _1-9 to 2-9 and the date as required. Personally I am not interested in the date but assuming that this works perfectly  as no doubt you intent it should be listed as a how to.  I am sure there are others like me who are looking hard for this.

---

### Post by lrgmmc on 2011-01-10
it looks like lame,mp3wrap and faac are missing.

---

### Post by lrgmmc on 2011-01-10
deleted.

---

### Post by lrgmmc on 2011-01-10
deleted.

---

### Post by lrgmmc on 2011-01-10
deleted.

---

### Post by lrgmmc on 2011-01-10
sorry for the multiple posts above.work internet is slows so i did what i always preach against....I kept clicking that mouse till somthing happend LOL.
any ways.
it looks like lame mp3wrap and faac are missing.
 
```
sudo apt-get install lame faac mp3wrap
```
 
also i did find a gui software that may be of some use.
 
[http://ubuntuforums.org/showthread.php?t=1431384](http://ubuntuforums.org/showthread.php?t=1431384)

---

### Post by Scunnered on 2011-01-10
**lrgmmc**

I followed your advise and downloaded the missing items and double checked that everything had downloaded properly.

When I follow your instruction ./audiobooker.sh Hitchhiker's auther year hitting enter produces >

Copying and re-entering the information produces 

"ian@ubuntu:~$ ./audiobooker.sh Hitchhiker's auther year
> ./audiobooker.sh Hitchhiker's auther year
bash: ./audiobooker.sh: No such file or directory
ian@ubuntu:~$ 

Using ./audiobooker.sh Hitchhiker's_1-5 auther year 2005
again produces the same error.

I must be doing something wrong somewhere but for the life of me I have no idea what. Should there be something before the "**./audiobooker.sh**"

I was under the impression the the DOT before a file name was a hidden file but my audiobooker.sh is in my /home folder and clearly on view.

I had a look the the link you posted and attempted to follow it but hit problems when it asked me to create something as the path was not found. Having hit this problem I will read through the complete thread and hope that I can understand what is involved.

The initial look appears not to link up all the tracks to form 1 track per CD.  This is the way that iTunes does things and it is a very easy way to listen and is my preferred option.

If you can set me on the road to resolving this problem with the missing file it will be appreciated.  As far as I can see initially your script looks to be the way to go.

Once again my sincere thanks for all your kind assistance

---

### Post by Scunnered on 2011-01-13
**lrgmmc**

I have read through the link "Howto: Create iPod-compatible m4b audiobooks with chapters and cover" but found that it did not quite follow what I was looking for.

What you offered initially looked ideal and if you can get me past the current road block it looks to be just what is needed.

I really hate the idea of having to buy another laptop just to have audio books work with Ubuntu.

I hope that you can resolve matters.

---

### Post by lrgmmc on 2011-01-13
I am currently working on a different approach. Check your pm's.

---

### Post by Scunnered on 2011-01-14
Received your PM and responded

---

### Post by darkmage_26 on 2011-03-03
simply need go in "Edit Track Details" menu of the file to me used as audio book. (this menu shall be available on pressing right click with pointer upon the file).
- Select "Media Type" as Audiobook
- check the block to "Remember Playback Position"
- Apply these changes pressing OK and that's it.

I hope this will work for you. It worked that way when my brother fixed his gtkpod. :P

---

### Post by Scunnered on 2011-03-04
**darkmage_26**

Thank you for your kind reply. I will give this a try and see how it works. 

I also looked at your links. I am informed by audible.co.uk that I need iTunes to use their services.  So far I am still having to borrow a windows system to keep working with audio books.

I hope that this will work and let me get totally away from doz.

Will advise further when I get things up and running

---

