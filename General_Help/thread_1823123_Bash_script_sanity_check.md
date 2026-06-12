---
title: "Bash script sanity check"
date: 2011-08-11
forum: General Help
---

### Post by krumpy on 2011-08-11
I haven't done a ton of scripting in bash and just wanted to sanity check this before I started using.  Right now it works fine, but just wanted to see if there was anything that could possibly cause trouble.  It's just supposed to copy the contents of my photo memory card, rename and move the photos then delete the temp directory.

```

#! /bin/bash
set -e
set -u
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games 
SOURCE_DIR=/media/CANON_DC/DCIM/
WORK_DIR=/home/matt/phototmp1
TARGET_DIR=/home/matt/Pictures
mkdir $WORK_DIR 
find $SOURCE_DIR -name "*.JPG" -type f -print0 | xargs -0 -I {} /bin/cp {} $WORK_DIR 
exiftool -v -d $TARGET_DIR/%Y/%m/%d/%Y%m%d_%H%M%S%%-c.%%e "-filename<CreateDate" $WORK_DIR 
rm -rf $WORK_DIR 

```

---

### Post by krumpy on 2011-08-11
An additional question for anyone else that has done something similar.  Is it possible to mark the photos on the photo card as having been read?  Otherwise if you forget to delete the photos from the memory card it will just recopy all of them and you'll have a bunch of duplicates.  I don't really want to delete the photos from the card automatically, since I could see the potential to lose photos if something goes wrong with the initial copy.

---

### Post by papibe on 2011-08-11
Some thoughts:

It is always a good practice to quotes your bash variables, e.g.:
```
mkdir "$WORK_DIR"
```

You can simplify your 'find' line by executing the copy in the find itself:
```
find "$SOURCE_DIR" -name '*.JPG' -type f -exec cp '{}' "$WORK_DIR" \;
```

Sorry to say that I haven't work with 'exiftool' so that part I wouldn't know what to say.

Regards.

---

### Post by papibe on 2011-08-11
> **krumpy said:**
> An additional question for anyone else that has done something similar.  Is it possible to mark the photos on the photo card as having been read? 
There's no way to do exactly that...

> **krumpy said:**
> I don't really want to delete the photos from the card automatically, since I could see the potential to lose photos if something goes wrong with the initial copy.
Most cameras number pictures in a sequence for example:
```
DSCF0001.JPG
DSCF0002.JPG
DSCF0003.JPG
...
```
My sister's camera will keep counting no matter what, making it more difficult to have 2 pictures with the same name. But my camera will use the lowest unused spot. For example if I delete one, let's say DSCF0002.JPG, the next picture will be save using that name (DSCF0002.JPG).

How does your camera manage that issue?

Regards.

---

### Post by krumpy on 2011-08-25
Thanks for the reply.  After some research it looks like my camera numbers photos 0001-9999.  So each picture gets pretty close to a unique number.  It seems like I could store the highest img number for given upload in a .txt file or something and then compare that to the img numbers of the files currently on the memory card.  I think I'm going to have to do some research to figure out how to go about that though.

---

