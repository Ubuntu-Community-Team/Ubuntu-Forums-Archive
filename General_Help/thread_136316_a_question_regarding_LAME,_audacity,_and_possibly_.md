---
title: "a question regarding LAME, audacity, and possibly gtkpod (if we have time)"
date: 2006-02-25
forum: General Help
---

### Post by ren wins on 2006-02-25
so i've got some .m4a files, and i want to try to convert them to .mp3 with audacity.  Audacity said it needed LAME to do it, and asked for the location of libmp3lame.so

i've installed LAME with synaptic (i totally forgot about it until now, i suppose i could use it to convert the .m4a's, but i'm used to GUI's (windoze) and terminal sometimes seems like it'd take too long, what with typing out each individual file for every conversion). I did 'locate libmp3lame.so' and found

laserwolf@violet:~$ locate libmp3lame.so
/usr/lib/libmp3lame.so.0.0.0
/usr/lib/libmp3lame.so.0

my question is, what are those zeros at the end of the file? why are there 2 versions of it? can i rename a copy of it w/o the zeros to make it work? will it work with the zeros?


and on a SLIGHTLY related note
when i try to synch databases btwn my ipod and gtkpod, it asks to create some folders in /media/ and/or locate iTunesDB in /media
i know where iTunesDB is (locate to the rescue!)
can i just mkdir /media/iPod/bla bla bla bla /iTunesDB and have everything be cool? i allways assumed that when a program (in windoze) wanted to install stuff, it did all sorts of complicated things... but from playing around w/ slocate, it seems that programs just sort of unpack their various components into various directories, and away they go. is this a correct (if not oversimplified) observation?

---

### Post by Jucato on 2006-02-25
Just point Audacity to either of the two and encoding to MP3 will work. What the difference is, I don't know either. but it just works so I'm fine by it. :D

Don't know about the 2nd question though.

---

### Post by Harleen on 2006-02-25
libmp3lame.so.0.0.0 is the actual library wanted. /usr/lib/libmp3lame.so.0 is just a link to that file. You can of course create another link named libmp3lame.so pointing to the same file.
Usually the numbers show the version of the file. But I doubt 0.0.0 is really meant to be a version number.
For example zlib is installed in Version 1.2.3, so the file is called libz.so.1.2.3. A link called libz.so.1 is created, to which applications that need zlib in Version 1.x get linked. If you later update the library all you have to do is to change the link. So it's possible to install many different versions of a library next to each other.

---

### Post by ren wins on 2006-02-26
thanks for the help!
once i pointed audacity in the right direction, it told me that it could not access the file?  i've been having trouble with the directories in my /media/ tree, mostly with ownership.  some programs can access them fine (nicotine or amarok, for example) and sometimes i can drag and drop files from my desktop into certain /media/ directories (they're all hard drive partitions.

what it comes down to is this (and i'll probably make a new thread asking this question in a minute)  how is it that my default (and only) user ID is not allowed into all the various groups or ownerships of my folders? how do i find out what groups i am a part of? and how do i change the ownership of directories so that i can write to them from where-ever i am?

---

### Post by Jucato on 2006-02-26
That's strange. I just installed the LAME encoder a few days ago and it worked fine with Audacity... Can you describe how you "pointed Audacity in the right direction"?

About the folders thingy. The only folder your user has authority on is it's own /home folder. All the rest belong to the root user (the administrator or super user), with the exception of /tmp, which is basically anybody's folder. Anything outside of /home/username, you'd be needing special permissions to use.

---

