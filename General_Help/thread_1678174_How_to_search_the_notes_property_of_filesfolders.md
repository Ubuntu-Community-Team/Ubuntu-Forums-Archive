---
title: "How to search the notes property of files/folders?"
date: 2011-01-29
forum: General Help
---

### Post by uberwulu on 2011-01-29
Ok here is my purpose:  I am running Ubuntu 10.10 and have a 2TB external hard drive where I store several hundred movies.  Each movie is contained in its own folder (in case the movie is broken up into more than 1 file).  All the movie folders are contained in one "Movies" folder, so a typical movie location would be something like:

/media/MyBook/Movies/The Matrix/The Matrix (disc1).avi

Because of this, my movies are in alphabetical order, which is nice if I'm looking for a specific movie, but I'd also like to classify each movie into one or more genres.  Sometimes I'm in the mood for a certain type of movie, and don't want to just browse aimlessly through the alphabetical list.  So for example, The Matrix might be classified as Action, Science Fiction, and Thriller.  If I were to add these genres into the "Notes" property of a movie folder, is it possible to conduct a search for words only in these notes?  So that if I did a search for "Thriller" this movie and any other movie I classified as a thriller would show up?

Thanks for any help.

---

### Post by InspiredIndividual on 2011-01-30
It might be possible to search the notes, but I do not know how. I do know two different ways that may offer you the required functionality, though.

Firstly, you could create a separate folder 'Genres' containing subfolders 'Thriller', 'Comedy', etcetera. In the subfolder 'Thriller', create softlinks to all movies with
```
ln -s {target-filename} {symbolic-filename}
```

Secondly, you could append a genre indication to the filename itself, for example moviename_thriller. This would make it very easy to find the files you're searching for.

---

### Post by uberwulu on 2011-01-30
Yeah I did consider doing that, and downloaded pyrenamer to help get the tedious task done more quickly.

I also found this tool called Tracker that supposedly lets you add tags to files and then search the tags, but I haven't figured out how to make it work yet.  I got it installed, the tags option appears in the context menu, I am able to assign tags to the movie folders, and I set it to index the external hard drive.  However, when I try to search for, say, "comedy," nothing comes up.  Not sure how to search the tags this way.

---

### Post by InspiredIndividual on 2011-01-31
I don't know pyrenamer, I mostly use the command line for text operations. I know almost nothing about the command line, but I did learn regular expressions, which is very useful in my experience. It enables you to do text replacements like renaming with a single line of code, and it is quite logical.

---

