---
title: "condensing .rars into one item"
date: 2006-03-04
forum: General Help
---

### Post by uberlinux on 2006-03-04
Hi everyone. 
I use torrents to get stuff like videos and whatnot, but sometimes the torrent is full of 14mb .rars.  I was told that you could condense them into one video using winrar, but I dont have any windows machines, does anyone know how to do it in linux?

---

### Post by nrwilk on 2006-03-04
did you try something like this:

```

cat file1.rar file2.rar file3.rar > condensed.rar

```

If you do it this way, they'll have to be be named in the order in which they should be concatinated.

I'm not sure this'll work.  But, I don't see why it wouldn't.

---

### Post by rattking on 2006-03-04
I am assuming you want one video file and not one huge rar file.. if thats the case your looking for unrar its in the non-free repository 
apt-get install rar unrar
unrar x file1.rar
is its command to decompress the rar archive

but I may be misunderstanding

---

### Post by nrwilk on 2006-03-04
I just thought he could combine them and then unrar them. :) 

But, maybe unrar will concat them too? :-D

---

### Post by uberlinux on 2006-03-06
bump for more ideas.  does anyone know what I mean about how usenet and bittorrent packaging videos that way?

---

### Post by kabus on 2006-03-06
rattking already posted a way to do it.
If unrar doesn't work you can try the nonfree rar package from multiverse, which sometimes works better with certain archives.

---

### Post by uberlinux on 2006-03-06
but his way I would end up with individual video files, right?  I wanted one full video

---

### Post by kabus on 2006-03-06
You'll get one full video if that's what's in the archives. Just try it.

---

### Post by nrwilk on 2006-03-06
I'm pretty sure that rattking means that the unrar program will also combine them into a single file in addition to unpacking them.

---

### Post by Princey on 2006-03-06
[QUOTE=uberlinux]but his way I would end up with individual video files, right?  I wanted one full video[/QUOTE]


Usenet among other bittorrent uploaders normally zip (most times using winrar) a video into several files that makes it easier to transfer as it reduces overhead bandwidth and makes it easier to recover corrupted packets during transfer. Even if you see, say a DVD-R movie broken into 78 pieces, it's just one huge video, 4.3GB or there about. To get the file unpacked into the huge movie, follow ratkins suggestion, I'll copy and paste his directions again for you but with a little bit more. Open a terminal and type in:

sudo apt-get install rar unrar

then press the enter key. Type in your password for root after you're returned to the prompt, change to the directory the files are downloaded into by typing the following: 

cd Movies 

assuming that the name of the folder is Movies

When you get there, type in:

unrar x file1.rar 

replace "x file1.rar" with the first name of the rar file (let's say it's a spiderman movie. it would be "say spiderman001.rar")

press enter when done


You can close the terminal, go to the folder when it's all done and your movie should be there waiting for you. Best of luck.

---

### Post by uberlinux on 2006-03-06
so I just have to do it for the first archive?  say this is what I get in a torrent:
piece1.rar
piece2.rar
piece3.rar
etc
etc

I just have to unrar the first one, and it will do all of the pieces?

---

### Post by Princey on 2006-03-06
[QUOTE=uberlinux]so I just have to do it for the first archive?  say this is what I get in a torrent:
piece1.rar
piece2.rar
piece3.rar
etc
etc

I just have to unrar the first one, and it will do all of the pieces?[/QUOTE]


Yes, precisely. Winrar (unrar) in that case does the rest internally by combining then extracting the file. With winzip, in an expanded archive, you have to type the name of the last file. Winrar, does the opposite. To expand a file from an an expanded archive (that's what the pieces are) you need to type in the name of the first part or piece of the archive. Good luck.

---

### Post by uberlinux on 2006-03-07
nice, thanks very much

---

### Post by Princey on 2006-03-07
[QUOTE=uberlinux]nice, thanks very much[/QUOTE]


You're welcome. Enjoy!

---

### Post by rattking on 2006-03-07
I should mention that with rar installed the gui program ark (archive manager) can now handle rar files.. if you dont like the command line :)

---

### Post by uberlinux on 2006-03-07
I'm just surprised that you only need to do the action to the first piece.

---

### Post by Princey on 2006-03-07
[QUOTE=uberlinux]I'm just surprised that you only need to do the action to the first piece.[/QUOTE]


Just shows how simple some things are. Does that mean you got it to work?

---

### Post by uberlinux on 2006-03-08
havent tried anything yet, just getting ready.  
Now if only something other than MPlayer woud play XVID.  I wonder why one app will take advantage of the codecs and the rest won't

---

### Post by Jucato on 2006-03-08
I'm sure that it works. Use Ark (KDE Archiving Tool) and make sure that unrar is installed (better install the unrar-nonfree as the unrar-free can't handel RAR version 3.0). Usually, files that are split into more than 1 rar file are named like this: file.rar, file.r00, file.r01, etc. You only need to open the one with .rar and extract it. Ark will automatically combine it all into one file (if it was meant to be one file) provided you have downloaded everything successfully.

Doesn't Kaffeine play XviD? I think that it should since XviD and DivX are practically the same codecs.

---

### Post by Barrakketh on 2006-03-08
[QUOTE=Fenyx]Use Ark (KDE Archiving Tool) and make sure that unrar is installed (better install the unrar-nonfree as the unrar-free can't handel RAR version 3.0). Usually, files that are split into more than 1 rar file are named like this: file.rar, file.r00, file.r01, etc. You only need to open the one with .rar and extract it. Ark will automatically combine it all into one file (if it was meant to be one file) provided you have downloaded everything successfully.[/quote]
I don't think it does.  I recently had an archive that was split into thirteen files, starting with foo.001.  Ark wouldn't handle it, but the unrar command would.

> Doesn't Kaffeine play XviD?
If the gstreamer plugin for it is installed.  It'll also play XViD if you're using the xine engine.

If you're using gstreamer and want it to play anything it supports, install the gstreamer0.8-plugins meta-package.  FYI, some gstreamer plugins are only available through the multiverse repository.  The XViD plugin is one of them.

---

### Post by Jucato on 2006-03-08
[QUOTE=Barrakketh]I don't think it does.  I recently had an archive that was split into thirteen files, starting with foo.001.  Ark wouldn't handle it, but the unrar command would.[/QUOTE]

Now that's strange... I was speaking from the experience of doing that two days ago, and just a few minutes ago to confirm it. I have unrar-nonfree installed, instead of the unrar-free version, if that matters.

---

### Post by stormyuk on 2007-01-17
> **Jucato said:**
> Now that's strange... I was speaking from the experience of doing that two days ago, and just a few minutes ago to confirm it. I have unrar-nonfree installed, instead of the unrar-free version, if that matters.

I am having terrible problems with Ark and Rar/Unrar (I too have unrar-nonfree installed) and can use the command line to extract multi file Rar's. If I try and use Ark on the same files which are named file_name_part1.rar, file_name_part2.rar etc etc Ark just ignores the rest of the files and extracts one rar.

Does anyone have any clue WHY this is happening? Is it a bug? Is it just my setup and if so what can I do to fix it?

](*,) 

Thanks,

Mike

---

### Post by martin.mev on 2007-10-20
Isnt there i smoother way to do this w/o sitting in the terminal?

---

### Post by Princey on 2007-10-30
Yes, you can installing winrar under wine and using it to extract the files.

---

### Post by Uncle_John on 2007-11-15
it's a bit old thread, but anyway

i hace similiar probelm, i downloaded some movie from the internet and then saw, that it is split into several rar files. Then i tried to do that thing with unrar-free, but nothing happens. I tried to install the nonfree version, but i just can't find it. I don't think there is a problem with respositories, or maybe i am wrong.

Can anyone help?:confused:

---

### Post by dbcalo on 2007-11-15
i just installed the rar archiver simply called "rar" in synaptic and all works fine. no need to do command line stuff. open the main rar file and extract.

---

### Post by Uncle_John on 2007-11-15
there is only unrar-free shown in my synaptic, no rar and no unrar-nonfree

i have all respositories included so i really can't see where the problem is

EDIT: problem solved:P thanks anyway

---

### Post by QwUo173Hy on 2007-12-23
This is simple on Gutsy. Once you have rar installed, just double click on the .rar file and you can extract your file with file roller. I've just done it here.

---

