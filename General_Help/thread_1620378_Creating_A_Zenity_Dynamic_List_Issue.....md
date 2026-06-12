---
title: "Creating A Zenity Dynamic List Issue...."
date: 2010-11-13
forum: General Help
---

### Post by Dart00 on 2010-11-13
Im having a slight issue with Zenity and i cant seem to figure it out, I thought i would make a post. I really have to get this solved. :(

Im trying to make a zenity list. Depending on certain conditions the list may be long or short. Instead of doing a CASE for each combination of entries that could happen with many zenity list statements, I wana have 1 zenity statement and use variables to populate the zenity fields.

I wrote this:

```
#!/bin/bash

A="True"

if [ "A" = "True" ]; then
   ITEM1="TRUE"
   ITEM2="SomeText"
   ITEM3="MoreText"
   ITEM4="TRUE"
   ITEM5="SomeText"
   ITEM6="MoreText"
else
   ITEM1="TRUE"
   ITEM2="SomeText"
   ITEM3="MoreText"
fi

CASE=$(zenity --list --title="Title" --text="Text" --radiolist --column="Pick:" --column="Column" --column="Column" $ITEM1 $ITEM2 $ITEM3 $ITEM4 $ITEM5 $ITEM6 )

exit
```

Now from what i can see this works great. If "A" equals true, Zenity generates a 2 row list, if its not, it generates a 1 row list using the SAME zenity statement! I could just add more ITEMx variables in the statement and make my dynamic lists longer.

The problem comes in if i try to make 2,3,5 and/or 6 have "spaces" in them, such as:

```
   ITEM1="TRUE"
   ITEM2="Some Text"
   ITEM3="More Text"
   ITEM4="TRUE"
   ITEM5="Some Text"
   ITEM6="More Text"
```

Now what happens is it treats "Some Text" as "ITEM1" AND "ITEM2" completely messes up my list.

How can i make "Some Text" only take up 1 variable (ex: ITEM2) with out populating ITEM2 and ITEM3?

Hope someone can figure this out...google wasn't much help eather :(

I tried putting the variables in ""'s but all that makes a extra radio button, such as 2 when there are only 1 rows generated.

---

### Post by Dart00 on 2010-11-13
Oh...finally figured it out

IFS=:

unset IFS

:D

---

