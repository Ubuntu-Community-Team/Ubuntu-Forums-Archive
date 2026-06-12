---
title: "Collecting contents of multiple folders into one folder"
date: 2012-05-11
forum: General Help
---

### Post by vichingo_nl on 2012-05-11
Hi,

I have the following situation:

A HD with a folder on it called Movies.
A MyBook World edition where it's folder Movies is nfs mounted into /$home/$user/Movies.

I want to leave all the data within their respected location, but I want to have the contents of the HD Movie folder show up in the mounted location.

Is this possible and if yes, how do I do this.

Please advise

---

### Post by papibe on 2012-05-11
Hi vichingo_nl. Welcome to the forums!

If I understand correctly you need both movie collections shown in your ~/Movie folder?

How about this:
```

~/Movies/library1    --> My Book
~/Movies/library2    --> Other HD
```
That something like that would help?
Regards.

---

### Post by vichingo_nl on 2012-05-11
Thanks for the quick answer, but I already tried something simular.. My issue is that I do not have to write to that folder, only read from it (XBMC) and that I want to have everything visible in one place. Writing happens on another level and to only one folder at a time. I just don't want to have to merge 2,5 TB.

---

### Post by papibe on 2012-05-11
Ohh, I see.

XBMC library problems... been there, done that ;) (when I changed some libraries from samba to nfs). I personally went the hardcore way by fixing directly the database and the thumbnails.

Let's try this idea: symbolic links.

Leave what you have on Movies right now (other HD I believe), and link the directories from My Book to it.

Test one directory movie:
```
cd Movies
ln -s /media/My\ Book/Movies/Star\ Wreck\ in\ the\ Pirkinning
```
Then get into XMBC to see if you can play the movie.

If that works, I can help you with a script to link all movies.

Tell us how it goes.
Regards.

---

