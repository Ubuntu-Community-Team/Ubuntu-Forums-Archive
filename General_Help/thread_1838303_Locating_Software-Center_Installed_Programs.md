---
title: "Locating Software-Center Installed Programs?"
date: 2011-09-03
forum: General Help
---

### Post by Valkyr333 on 2011-09-03
Hi, all...

So lately I've been needing a program in my Kubuntu machine that will convert files from one format to another. I found one that looks just right (pacpl) and installed it from Ubuntu Software Center. Problem is, I can't find it anywhere in my Kickoff Menu, and Software Center doesn't seem to tell you in which directory it has placed installed programs. Now that I've installed this program, how do I find it?

Thanks!

-Val

---

### Post by 2F4U on 2011-09-03
Maybe it is a program without GUI interface? Anyways, open a terminal and execute whereis. For example, in order to search for kate (the editor) issue the following command:

```
whereis kate
kate: /usr/bin/kate /usr/share/man/man1/kate.1.gz

```

If a program is not installed you get an output similar to this

```
whereis jane
jane:

```

---

### Post by Valkyr333 on 2011-09-03
That returns,

```
pacpl: /usr/bin/pacpl /etc/pacpl /usr/share/pacpl /usr/share/man/man1/pacpl.1.gz

```

I'm not sure what this data tells me about how to access the program, though. Would I just go into that specific folder, drag and drop pacpl to a location like my "favorites" menu, or something? Or maybe right-click and "add to taskbar menu" somehow?

*Edit - The last part of that is "pacpl.1.gz" - Does that mean it needs to be unpacked first, somehow, or am I confusing terms?

---

### Post by 2F4U on 2011-09-03
I have no idea what pacpl is but this site suggests that it is a command line tool

[http://edigitales.org/perl-audio-converter-pacpl-multi-purpose-audio-converter-tagger-ripperscript/](http://edigitales.org/perl-audio-converter-pacpl-multi-purpose-audio-converter-tagger-ripperscript/)

So there is no GUI and the tool can be run from a terminal. The link I posted has some examples on how to use the script.

---

### Post by Valkyr333 on 2011-09-03
pacpl is a file conversion program which changes media files from one format to another.


The website in the link says,



"Pacpl script can be executed using the pattern:

*pacpl – to format options [file (s) / directory (s)]*


Examples of the use of this time are the conversion from mp3 to ogg format:


Suppose we have a collection of audio files in mp3 format which is located in the directory:

[I]* / Home/wdzgouch/Music/mp3/Alternative
 * / Home/wdzgouch/Music/mp3/Jazz[/I]


Furthermore, those files will be converted into audio files to ogg format to be stored in the directory:

[I]* / Home / wdzgouch / Music / ogg / Alternative
 * / Home / wdzgouch / Music / ogg / Jazz[/I]


To do convert the above scenarios run the command:
*pacpl – to ogg-r-p / home/wdzgouch/Music/mp3 – OutDir / home / wdzgouch / Music / ogg*


By  using the above command, then all the mp3 file is located in the  directory / home/wdzgouch/Music/mp3/Alternative and Jazz will be  converted into ogg file and the result will be stored in the directory /  home / wdzgouch / Music / ogg / Alternative and Jazz."


I'm a bit hung up on this list of instructions. The command line, 


```
pacpl – to ogg-r-p / home/wdzgouch/Music/mp3 – OutDir / home / wdzgouch / Music / ogg
```

doesn't mention the folders "Alternative" or "Jazz" anywhere, and even though those seem to be listed as two separate folders in the example:

[I]* / Home/wdzgouch/Music/mp3/Alternative
 * / Home/wdzgouch/Music/mp3/Jazz[/I]

the author seems to claim that running said code will result in the converted files being placed into one folder, which will be labeled as "Alternative and Jazz." Does the system assume these things automatically, or was it an error on the part of the author giving the instructions on that site? Or maybe, "Other"?

---

### Post by haresear on 2011-09-03
> **Valkyr333 said:**
> 
I'm a bit hung up on this list of instructions. The command line, 


```
pacpl – to ogg-r-p / home/wdzgouch/Music/mp3 – OutDir / home / wdzgouch / Music / ogg
```

doesn't mention the folders "Alternative" or "Jazz" anywhere, and even though those seem to be listed as two separate folders in the example:

[I]* / Home/wdzgouch/Music/mp3/Alternative
 * / Home/wdzgouch/Music/mp3/Jazz[/I]

the author seems to claim that running said code will result in the converted files being placed into one folder, which will be labeled as "Alternative and Jazz." Does the system assume these things automatically, or was it an error on the part of the author giving the instructions on that site? Or maybe, "Other"?

I haven't used this program, but I would guess that it will search all subdirectory paths below the input directory you give it for mp3 files, and replicate that subdirectory hierarchy in the output directory you give it, with the converted files arranged as in the original subdirectory structure.

---

### Post by Valkyr333 on 2011-09-03
That makes sense. I guess unless I know for sure, I might be wiser uninstalling pacpl and searching for a program for the same purpose that actually has a GUI. I'm just starting to learn the basics of programming now and I'm not really feeling confident enough to do anything that might risk screwing up my computer.

Thanks for your info/help. =)

---

