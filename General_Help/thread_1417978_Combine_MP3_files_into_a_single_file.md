---
title: "Combine MP3 files into a single file?"
date: 2010-02-28
forum: General Help
---

### Post by Nick_Jinn on 2010-02-28
I have an audiobook in 64 small mp3 files and I need them combined into a single file of any format in the proper order or order that I add them in.

What program can I use?

---

### Post by PsychoDevon on 2010-02-28
If you want to use an archive, make a new folder and copy all of the songs you need to combine and right-click on the folder and select 'Compress'. Then, you get a prompt asking you to name it and select what archive type, such as .tar.gz, .zip, etc.

---

### Post by Nick_Jinn on 2010-02-28
I dont think that is very helpful. You cant play a compressed file without uncompressing it, and then its 64 files all over again. 

I want to listen to this audiobook on my MP-3 player without worrying about it playing them out of order (Which it unfortunately does).

I am not trying to compress 64 files, I am trying to merge 64 files into 1 MP3 file.

---

### Post by hwttdz on 2010-02-28
It looks like mp3wrap would be the weapon of choice - 
[http://www.ubuntuhowtos.com/howtos/merge_mp3](http://www.ubuntuhowtos.com/howtos/merge_mp3) with a bit of scripting you 
can probably get this to go pretty well.

You could probably also use audacity (or any other audio editor), but it will be a little more involved.

---

### Post by Nick_Jinn on 2010-02-28
Those are possibilities but not great options. I am not a computer geek (And I use that term with respect). I am just a poor college student who runs a home business and is trying to support a family who likes open source anything due to his anti-corporate values, but doesnt really have a knack or any great interest in scripting commands. 

Audacity looks very complicated and scared me off when I tried to use it.


Isnt there anything more simple, like DeVeDe only for audio files? That would be awesome. 


Also, it needs to combine them in the proper order of the users choosing, not just combine them alphabetically or however they do it.

---

### Post by moe46 on 2010-02-28
Just do it from the terminal with cat

$cat *.mp3 > new_filename.mp3

That will just merge them all in to one file. It will merge them in some order not sure you can see it beforehand with 

$echo *.mp3

If the order isn't what you want, then you can do it a few at a time like,

$cat file1.mp3 file2.mp3 > new_file1.mp3

Good Luck

---

### Post by elliotn on 2010-02-28
If I were u, I'll use a Djing software or Audacity and join em into 1 track.

---

### Post by rahilm on 2010-02-28
> **Nick_Jinn said:**
> Those are possibilities but not great options. I am not a computer geek (And I use that term with respect). I am just a poor college student who runs a home business and is trying to support a family who likes open source anything due to his anti-corporate values, but doesnt really have a knack or any great interest in scripting commands. 

Audacity looks very complicated and scared me off when I tried to use it.


Isnt there anything more simple, like DeVeDe only for audio files? That would be awesome. 


Also, it needs to combine them in the proper order of the users choosing, not just combine them alphabetically or however they do it.
 
what's wrong with mp3wrap??

---

### Post by elliotn on 2010-02-28
Audacity is the simplest one

Just drop the tracks in audacity and then arrange em the way u like em, then when u happy export em to your favourate format.

---

### Post by Nick_Jinn on 2010-02-28
I have layered music with Audacity before, but how do you put them in order, one starting where the other stops?

I dont want to use the command line, not only because its more difficult for a non computer-geek but the lack of interface means that if they were out of order I would have to listen to 5.5 hours of material before I would be able to figure out what happened, and even then I wouldnt necessarily know what order it was supposed to be in. 

So I have Audacity open.....How does this work?

---

### Post by Nick_Jinn on 2010-02-28
I am looking at the Wiki, and there is a section for splitting recordings into seperate tracks but nothing on adding them....This should be easy I am thinking but I am not seeing how to do it.

I try opening a second file and instead of opening it in the same application it opens a whole new one that is separate.


How does this work?

---

### Post by asmoore82 on 2010-02-28
you could use `sox` - but you have to make sure to install the mp3 libs for it...
```
sudo apt-get install sox libsox-fmt-mp3
```

Then you can combine multiple mp3's into one wav or ogg like this
```
sox 1.mp3 2.mp3 3.mp3 123.wav
sox 1.mp3 2.mp3 3.mp3 123.ogg
```

In the *buntu packaging, `sox` will not create MP3's.
For maximum MP3 play compatibility, I would suggest making a wav with `sox`
and turning that to an MP3 with lame or audacity.

---

### Post by x C0MMAND0 x on 2010-02-28
How are they named?  Is it 1. Part 1, 2. Part 2 etc?  If they are already in order, why not send them all into an archive, upload them here, and I will merge them for you.

---

### Post by Nick_Jinn on 2010-02-28
So it wont work with MP3s?


How do I add the files? When I cut and paste the page of links it looks like this....



/home/djinn/Downloads/Sailor/Sailor-0.mp3
/home/djinn/Downloads/Sailor/Sailor-1.mp3
/home/djinn/Downloads/Sailor/Sailor-2.mp3
/home/djinn/Downloads/Sailor/Sailor-3.mp3
/home/djinn/Downloads/Sailor/Sailor-4.mp3
/home/djinn/Downloads/Sailor/Sailor-5.mp3
/home/djinn/Downloads/Sailor/Sailor-6.mp3
/home/djinn/Downloads/Sailor/Sailor-7.mp3
/home/djinn/Downloads/Sailor/Sailor-8.mp3
/home/djinn/Downloads/Sailor/Sailor-9.mp3
/home/djinn/Downloads/Sailor/Sailor-10.mp3
/home/djinn/Downloads/Sailor/Sailor-11.mp3
/home/djinn/Downloads/Sailor/Sailor-12.mp3
/home/djinn/Downloads/Sailor/Sailor-13.mp3
/home/djinn/Downloads/Sailor/Sailor-14.mp3
/home/djinn/Downloads/Sailor/Sailor-15.mp3
/home/djinn/Downloads/Sailor/Sailor-16.mp3
/home/djinn/Downloads/Sailor/Sailor-17.mp3
/home/djinn/Downloads/Sailor/Sailor-18.mp3
/home/djinn/Downloads/Sailor/Sailor-19.mp3
/home/djinn/Downloads/Sailor/Sailor-20.mp3
/home/djinn/Downloads/Sailor/Sailor-21.mp3
/home/djinn/Downloads/Sailor/Sailor-22.mp3
/home/djinn/Downloads/Sailor/Sailor-23.mp3
/home/djinn/Downloads/Sailor/Sailor-24.mp3
/home/djinn/Downloads/Sailor/Sailor-25.mp3
/home/djinn/Downloads/Sailor/Sailor-26.mp3
/home/djinn/Downloads/Sailor/Sailor-27.mp3
/home/djinn/Downloads/Sailor/Sailor-28.mp3
/home/djinn/Downloads/Sailor/Sailor-29.mp3
/home/djinn/Downloads/Sailor/Sailor-30.mp3
/home/djinn/Downloads/Sailor/Sailor-31.mp3
/home/djinn/Downloads/Sailor/Sailor-32.mp3
/home/djinn/Downloads/Sailor/Sailor-33.mp3
/home/djinn/Downloads/Sailor/Sailor-34.mp3
/home/djinn/Downloads/Sailor/Sailor-35.mp3
/home/djinn/Downloads/Sailor/Sailor-36.mp3
/home/djinn/Downloads/Sailor/Sailor-37.mp3
/home/djinn/Downloads/Sailor/Sailor-38.mp3
/home/djinn/Downloads/Sailor/Sailor-39.mp3
/home/djinn/Downloads/Sailor/Sailor-40.mp3
/home/djinn/Downloads/Sailor/Sailor-41.mp3
/home/djinn/Downloads/Sailor/Sailor-42.mp3
/home/djinn/Downloads/Sailor/Sailor-43.mp3
/home/djinn/Downloads/Sailor/Sailor-44.mp3
/home/djinn/Downloads/Sailor/Sailor-45.mp3
/home/djinn/Downloads/Sailor/Sailor-46.mp3
/home/djinn/Downloads/Sailor/Sailor-47.mp3
/home/djinn/Downloads/Sailor/Sailor-48.mp3
/home/djinn/Downloads/Sailor/Sailor-49.mp3
/home/djinn/Downloads/Sailor/Sailor-50.mp3
/home/djinn/Downloads/Sailor/Sailor-51.mp3
/home/djinn/Downloads/Sailor/Sailor-52.mp3
/home/djinn/Downloads/Sailor/Sailor-53.mp3
/home/djinn/Downloads/Sailor/Sailor-54.mp3
/home/djinn/Downloads/Sailor/Sailor-55.mp3
/home/djinn/Downloads/Sailor/Sailor-56.mp3
/home/djinn/Downloads/Sailor/Sailor-57.mp3
/home/djinn/Downloads/Sailor/Sailor-58.mp3
/home/djinn/Downloads/Sailor/Sailor-59.mp3
/home/djinn/Downloads/Sailor/Sailor-60.mp3
/home/djinn/Downloads/Sailor/Sailor-61.mp3
/home/djinn/Downloads/Sailor/Sailor-62.mp3
/home/djinn/Downloads/Sailor/Sailor-63.mp3
/home/djinn/Downloads/Sailor/Sailor-64.mp3

Is that the right format for combining them?

I have to turn them into an different format first? That sounds very difficult for something that should be simple.

If somebody could tell me how to sequence my audiobook chapters in order into a single file with Audacity, that would be helpful.

---

### Post by Nick_Jinn on 2010-02-28
> **x C0MMAND0 x said:**
> How are they named?  Is it 1. Part 1, 2. Part 2 etc?  If they are already in order, why not send them all into an archive, upload them here, and I will merge them for you.


No ****?!

Thanks!!!
I have a Rar or I can send you the Archive.....


I will send you the first book as well, so you can get something for your efforts. How should I send it to you?

---

### Post by x C0MMAND0 x on 2010-02-28
> **Nick_Jinn said:**
> No ****?!

Thanks!!!
I have a Rar or I can send you the Archive.....


I will send you the first book as well, so you can get something for your efforts. How should I send it to you?

Just upload it through the forums in whatever archive you want.  If that doesn't work, let me know.

---

### Post by x C0MMAND0 x on 2010-02-28
EDIT: I just realized they are probably much larger than the maximum upload size of the forums.  I will PM you my email address and you can send it to me.

---

### Post by Nick_Jinn on 2010-02-28
Its the Elric Saga btw by Micheal Moorcock. Its a classic if you are into that sort of literature. Its a little cheesy sometimes and quite dark, but its wildly entertaining.

---

### Post by x C0MMAND0 x on 2010-03-01
Okay, I know you said you don't like terminal/command line, but it is the only way.  Here are some VERY simple steps.

1. Make sure to make a copy of your /home/djinn/Downloads/Sailor/ folder, but be sure not to alter that folder in any way and keep all of the files there, because I wrote this script based on it.

2. Download the folder I attached here and extract the file called "combinefile.sh" and save it to your DESKTOP. This is important.

3. Click on "Applications" > "Accessories" > "Terminal"

4. Paste the following code into the terminal and hit enter
```
cd /home/djinn/Destkop
```

5. Paste the following code into the terminal and hit enter 
```
chmod +x combinefile.sh
``` 

6. Paste the following code into the terminal and hit enter ```
./combinefile.sh
``` 

Look in your /home/djinn/Downloads/Sailor/ folder for a file called "MASTER.mp3"

Please let me know if this works and if you have any questions.

---

### Post by x C0MMAND0 x on 2010-03-01
I'm curious to know how the script worked out for you...

---

### Post by Nick_Jinn on 2010-03-02
I am trying it now. I really appreciate you putting out the effort.

---

### Post by Nick_Jinn on 2010-03-02
Step one failed, probably because its not a CD. I downloaded the MP3 version from the site that was also selling the CDs.


> djinn@Anon:~$ cd /home/djinn/Destkop
bash: cd: /home/djinn/Destkop: No such file or directory


---

### Post by Nick_Jinn on 2010-03-02
Or maybe its because Desktop was spelled wrong.


> 
[FONT=monospace]djinn@Anon:~$ cd /home/djinn/Desktop
djinn@Anon:~/Desktop$ chmod +x combinefile.sh
chmod: cannot access `combinefile.sh': No such file or directory
djinn@Anon:~/Desktop$ combinefile.sh
combinefile.sh: command not found


[/FONT]

---

### Post by x C0MMAND0 x on 2010-03-02
Did you put the "combinefile.sh" on your DESKTOP?  You have to extract it from the archive.  Then run the following:

```
chmod +x combinefile.sh
```

Then run the following...

```
./combinefile.sh
```

Also, the "CD" command I had stands for **C**urrent **D**irectory, it has nothing to do with a physical compact disc, just FYI.

---

### Post by x C0MMAND0 x on 2010-03-02
If you cant figure that out, try this.

1. Extract the "combinefile.sh" to your desktop.

2. Right click on the file, go to "Properties", go to the "Permissions" tab, and CHECK the box that says "Allow executing file as program", then close out.

3. Double click on the "combinefile.sh" and then click on the option that says, "Run in terminal".

---

### Post by RMZindorf on 2010-03-02
Audacity. It will be the easiest way to get it done. If my gf can do it you can do it!

---

### Post by Enigmapond on 2010-03-02
+1 Audacity does this just great. I have done it and it's easy and very good.

---

### Post by Nick_Jinn on 2010-03-03
I finally figured it out, sort of.

---

### Post by x C0MMAND0 x on 2010-03-03
> **Nick_Jinn said:**
> I finally figured it out, sort of.

Did my script work then?  Why just "sort of"?

---

### Post by x C0MMAND0 x on 2010-03-06
? What's the status?

---

### Post by airplus on 2010-04-02
> **rahilm said:**
> what's wrong with mp3wrap??


Thanks for your suggestion, I have just joined up 490 mp3 audiobooks with it, thanks!!!

---

### Post by yourseolab1 on 2010-05-06
The method of joining is a bit smarter. MP3 files can be combined  directly, without converting them to WAV and back. With this method, audio data  from separate files is copied into a single MP3 file. This method is not only  better because of preserving the original quality, but it is also much quicker. [mp3 editor]("http://mp3do.com/soundeditor.html")uses the direct MP3 joining method.

---

### Post by Teodor605 on 2011-11-30
I know this thread is getting old now. But anyhow, actually there is a MUCH easier way to do this :P

I used to let Audacity take care of joining multiple mp3 tracks when making my own audiobooks. But it takes forever and uses a lot of computer time and space. There is a GUI based program for Windows called mp3merge.exe which can be found [here]("http://www.hitsquad.com/smm/programs/MP3Merger/"). If you have Wine or anything else installed then you can also use it on a PC running Ubuntu.

mp3merge will join all files into one in the sort order you like. And it uses the id3 tags from the first of the original files to be joined.

If you want to convert the mp3 file into something else you may use Audacity for that. Or any other file converter. However I would not recommend Audacity for joining literally hundreds of 5-minute mp3 files:rolleyes:

---

### Post by Teodor605 on 2011-11-30
Edit: The easiest way to obtain the file is to click on the link to the developer's website. Clicking on the "download" link did not produce any download when I tried it out just now. But the developer's own site did. Maybe it's just because I am new to Ubuntu and didn't find any download bar like in Windows :(

---

