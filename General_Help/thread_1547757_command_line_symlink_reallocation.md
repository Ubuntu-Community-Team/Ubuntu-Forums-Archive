---
title: "command line symlink reallocation"
date: 2010-08-07
forum: General Help
---

### Post by momist on 2010-08-07
Good morning everyone,

I'm running a clean install of Lucid on a new HD.  I've moved over all my old data and files from the previous Karmic system, and am having trouble with a directory full of symlinks.  This is a collection of links into my photographs, which I use for wallpaper with Desktop Drapes, and the directory has 1300 symlinks which now point to the wrong place.  

I only need to change the first part of the link target:
/oldplace/somedir/subdir/photo.jpg
into:
/newplace/somedir/sudir/photo.jpg

I believe this needs the application of _  ln  _  in a terminal to re-write the symlink, and the use of a bash line including  _ if  . . fi  _  or possibly _  IFS _ ?  I might also need to use _  sed,  - but I'm not sure of the syntax for this.

Can anyone offer some guidance please?

Ian

---

### Post by DaithiF on 2010-08-07
Hi,
cd to the directory then do something like this:

```

for file in *
do
if [[ -h "$file" ]]; then
  target=$(readlink "$file")
  newtarget=$(target/oldplace/newplace}
  echo ln -fs "$newtarget" "$file"
fi
done

```
remove the echo once you're happy its doing the right thing

---

### Post by momist on 2010-08-09
> **DaithiF said:**
> Hi,
cd to the directory then do something like this:

```

for file in *
do
if [[ -h "$file" ]]; then
  target=$(readlink "$file")
  newtarget=$(target/oldplace/newplace}
  echo ln -fs "$newtarget" "$file"
fi
done

```
remove the echo once you're happy its doing the right thing

Sorry to go away on this - I have a domestic crisis which took me off the hobby and onto DiY.  The soil pipe from the bathroom is leaking!   :(

However, I did try your idea and can't get it to work.  I've been messing around with readlink (which is the bit I didn't know about) and think that once I've mastered some more bash string handling I'll be able to do this now.  I just don't have the time to learn at the mo.

Thanks for the help anyway!  I'll post back with the solution if I reach one.

---

### Post by DaithiF on 2010-08-09
ah, i see a typo in my previous post:
newtarget=$(target/oldplace/newplace}
should be:
newtarget=${target/oldplace/newplace}

---

