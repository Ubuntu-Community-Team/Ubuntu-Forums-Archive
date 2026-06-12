---
title: "how do I do this in terminal? I need more help"
date: 2011-03-20
forum: General Help
---

### Post by twodogs on 2011-03-20
First, this is what I do...

I have two external hard drives with movies on each and the movies are in a folder called 'movies.'

I use this command --> 
ls /media/ONETOUCH/movies > ~/Documents/Movie_List_1.txt  (alias=movielist1)

for external drive one.

and this command --> 
ls /media/MOVIES_2/movies > ~/Documents/Movie_List_2.txt  (alias=movielist2)

for external drive two.

Now I have two files in my Documents folder called 'Movie_List_1.txt' and 'Movie_List_2.txt'

---------------------------------------------------

This is what I want to accomplish...

I want to use an alias (movielist) to join these two files (Movie_List_1.txt and Movie_List_2.txt) and save the file as 'Movie_List.txt'

This 'Movie_List.txt' file should include all movies from both lists and they should be in alphabetical order.

I use this alias to see all my movies in a terminal --> allmymovies="cat ~/Documents/Movie_List.txt | less"

I have it all working fine except the part where it will combine the two text files and in alphabetical order.

Do you know how to do this and if so, could you show me how?  I have searched high and low on the internet but can't seem to find a good example.

Thanks for your time.

---

### Post by papibe on 2011-03-20
Is this a homework assignment?

Anyway, check the sort command:
```
$ man sort
```

Good Luck!

---

### Post by cjhabs on 2011-03-20
sort Movie_List_1.txt Movie_List_2.txt > Movie_List.txt

---

### Post by idoitprone on 2011-03-21
cat also works. I use cat to join split rar files from mega upload or other file sharing sites

cat Movie_List_1.txt Movie_List_2.txt | sort  > Movie_List.txt

nevermind, you want it in alphabetical order, so which mean you end up piping though sort

---

### Post by twodogs on 2011-03-21
Thanks for your help. LOL homework assignment.  No, it's not homework.  Thanks again, big help!

---

