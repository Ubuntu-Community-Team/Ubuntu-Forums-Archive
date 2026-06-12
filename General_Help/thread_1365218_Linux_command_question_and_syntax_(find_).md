---
title: "Linux command question and syntax (find ?)"
date: 2009-12-26
forum: General Help
---

### Post by luke0927 on 2009-12-26
OK becasue of all the freezing I had to blow away 9.10 and go back to 9.04.  I have a lot of music that i want to sort into folders of the artist name...Is there a way I can use the find command to find files with the artist name or part of it if i use an * and then copy them to the folder? So in the end I would like to have folder of all artist name and then the songs by the artist in the file....(most of the song's saved name have part of the artist name in them)

Thanks

---

### Post by hwttdz on 2009-12-26
Well there are probably hundreds of ways, I might use ls instead of find.

ls -Q|grep -i "artisname"|xargs mv -t artistname_folder

I think the find solution you're looking for is something along the lines of 

find . -name "artistname" -exec command (where command moves the file to the folder of interest, I don't know the exact syntax for that part of find, but man find is pretty extensive if I remember correctly).

---

### Post by luke0927 on 2009-12-26
It does'nt have to be a find command just something to make it work...I'm just a beginer so not reall sure what to use...I basically want to tell it to seach a directory XYZ and when you find the string requested move it to director ABC with the same name.....I'll see what I can do with the command you posted....also is there a syntax I can use to make it not care about case sensitivity

Thanks!

---

### Post by hwttdz on 2009-12-26
So half the reason I defaulted to the ls command with grep is because I use grep frequently and therefore remembered that -i is the flag for case insensitive.  

So explaining my previous command

ls -Q|grep -i "artisname"|xargs mv -t artistname_folder

we have ls -Q, which says list all the files and quote them (to deal with spaces and funny characters in the filenames).  You might change this to ls -Q *.mp3 which lists just the mp3 files (this will also avoid the, can't move the folder to inside itself error).  

the | is a pipe it sends the output of one command to the next

the next command is grep, it searches for a string in the input (or file), in this case is performs a case insensitive search for "artistname", so the contents of the next pipe is a quoted list of all the files which contain artistname (case insensitive)

and the final command uses xargs (which takes the output and sends it as arguments to the next command), then mv (move), -t (target) here the target is the folder we want the files to end up in, and finally xargs lists the files, so the command executed is 

mv -t artistfolder Artistsong1.mp3 arTisTSong2.mp3 ...

which moves all those songs to that folder.

The find command is somewhat more intuitive, finding all files matching a pattern and executing a command on them (in this case move).

You could probably also run something like "mv artistname*.mp3 foldername".  And any number of other command to do the same thing (clever perl oneliner anyone?).

---

### Post by luke0927 on 2009-12-27
OK got it to work with this just have to change the name for each artist after I make my directory

find /home/luke/Music/ -iname "*shooter*.mp3" -exec mv -v {} ~/Music/Shooter\ Jennings \;

---

