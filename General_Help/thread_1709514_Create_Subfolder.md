---
title: "Create Subfolder"
date: 2011-03-18
forum: General Help
---

### Post by nd0627 on 2011-03-18
Hi ! I want to do this within the least time possible.

I have around 100+ folders in which I need to create a subfolder of the same name. How do I do this ?


Thanks in advance !!!

---

### Post by nothingspecial on 2011-03-18
If they are all in the same parent directory then

```
for d in *; do mkdir "$d"/blah; done
```

issued from that directory.

change blah for the directory you want to create inside each one.

Don't just copy and paste stuff I say just because I have a lot of posts, test it.

---

### Post by nothingspecial on 2011-03-18
The previous example will make a directory called blah in every directory.

eg

dir1/blah
dir2/blah
dir3/blah
etc

```
for d in *; do mkdir "$d"/"$d"; done
```


That one will make a directory named the same as the one above it in every directory. 

eg 

dir1/dir1
dir2/dir2
dir3/dir3
etc

I am unsure which you mean.

---

### Post by Telengard C64 on 2011-03-18
Don't do this!
(Mod note: the referenced post has been removed - drs305)
VVVVVVVVVVVVVV

> **TeoBigusGeekus said:**
> ...or you could use find once in the parent directory
```
find ./ -type d -exec mkdir "{}/nameofnewdir" \;
```

^^^^^^^^^^^^^^
Don't do that! It will recursively create nested directories until the command fails due to the extremely long pathname.

A *less unsafe* invocation of the **find** command *might* look something like this:

```
find -mindepth 1 -maxdepth 1 -type d -exec mkdir '{}/nameofnewdir' \;
```

nothingspecial's solution seems more sensible anyway.

```
foo$ for d in *; do mkdir -v "$d"/"$d"; done
mkdir: cannot create directory `01-Sonata In D minor BWV964 Adagio (JS Bach)-Colin Booth.wav/01-Sonata In D minor BWV964 Adagio (JS Bach)-Colin Booth.wav': Not a directory
mkdir: cannot create directory `02-Sonata In D minor BWV964 Allegro (JS Bach)-Colin Booth.wav/02-Sonata In D minor BWV964 Allegro (JS Bach)-Colin Booth.wav': Not a directory
mkdir: created directory `one/one'
mkdir: created directory `three/three'
mkdir: created directory `two/two'
foo$
```

The only drawback is that the **for** loop is not just selecting directories, it is also selecting regular files. This can easily be worked around by adding a **test** to check whether ***** matched a directory or regular file name.

```
foo$ for d in * ; do if [ -d "$d" ] ; then mkdir -v "$d"/"$d" ; fi ; done
mkdir: created directory `one/one'
mkdir: created directory `three/three'
mkdir: created directory `two/two'
foo$
```

HTH

---

### Post by TeoBigusGeekus on 2011-03-18
> **Telengard C64 said:**
> It will recursively create nested directories until the command fails due to the extremely long pathname.

Yes, I'm sorry for that.
Why does it happen though?

---

### Post by aktiwers on 2011-03-18
Sorry to be offtopic, but TeoBugusGeekus.. have you seen this?
[http://www.omgubuntu.co.uk/2011/03/autocad-clone-draftsight-hits-linux-beta/](http://www.omgubuntu.co.uk/2011/03/autocad-clone-draftsight-hits-linux-beta/)

Not an autocad user, but still looks promising..

---

### Post by nothingspecial on 2011-03-18
> **TeoBigusGeekus said:**
> Yes, I'm sorry for that.
Why does it happen though?

Because
[B]
I think[/B]

find acts on one result at a time and recursively. So it creates a directory in the first directory it finds and will then find that directory and create a directory in that one and so on and so on until your computer blows up.

I once completely destroyed a perfect (in my eyes) system using find.

---

### Post by TeoBigusGeekus on 2011-03-18
> **nothingspecial said:**
> Because
[B]
I think[/B]

find acts on one result at a time and recursively. So it creates a directory in the first directory it finds and will then find that directory and create a directory in that one and so on and so on until your computer blows up.

I once completely destroyed a perfect (in my eyes) system using find.

Thanks for that...
It's the first time 'find' backfires on me like that; I find it convenient and use it all the time-I have probably been lucky :p

@aktiwers: Thanks for the link, but comparing Draftsight, Bricscad, Qcad, Brlcad, etc. with their commercial equivalents is like comparing a Yugo with a Ferrari. 
Thanks for the interest though, I appreciate it.

---

### Post by nothingspecial on 2011-03-18
[SIZE="3"][COLOR="Red"]Don't do either of these[/COLOR][/SIZE]

See how a tiny difference can change things

```
find ./ -type f -exec mv '{}' ./ \; 
```


```
find / -type f -exec mv '{}' ./ \;
``` 

The incorrect (system hosing) one would fail without sudo on a standard Ubuntu installation, but that is not the point. The point is in my sig. :D

Even the non-system-hosing one would destroy your installation issued from the wrong directory. ICBIST but find is powerfull.

---

### Post by Telengard C64 on 2011-03-18
> **nothingspecial said:**
> find acts on one result at a time and recursively. So it creates a directory in the first directory it finds and will then find that directory and create a directory in that one and so on and so on until your computer blows up.

That is quite correct (except the computer won't *literally* blow up of course). **find** is *recursive by default* unless you limit it somehow. The **-maxdepth** and **-mindepth** options in my example do the job here.

> I once completely destroyed a perfect (in my eyes) system using find.

Sorry for that. Any software can be potentially destructive when used naively. The only way to be *safe* is to educate yourself in the proper use of your software.

Of course, sometimes *education* includes learning from mistakes  ;)

---

### Post by TeoBigusGeekus on 2011-03-18
If it still matters (and also to soothe my broken ego and self esteem), this would work correctly:
```
find ./ -type d ! -name "dir" -exec mkdir '{}'/dir \;
```

I need affection and a hug...:cry:
(boo hoo... forever alone)

EDIT: Thanks for the explanation Telengard.
Once again, sorry for any inconvenience caused.

---

