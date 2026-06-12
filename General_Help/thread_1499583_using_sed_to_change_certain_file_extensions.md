---
title: "using sed to change certain file extensions?"
date: 2010-06-02
forum: General Help
---

### Post by rebeltaz on 2010-06-02
I have about a hundred and fifty html files that I would like to change image file extension on from gif to png. I want to change this line:

<img src="images/robopix/web/ROBOTNAME.gif" border="0">

to this:

<img src="images/robopix/web/ROBOTNAME.png" border="0">

Trouble is that ROBOTNAME is different in each of the hundred and fifty files. To make it harder, there are other gif filenames on these pages that I do not want to change. I only want the extensions to change if the address prefix is 'images/robopix/web/'. 

Is there any way to do this with a quick program/sed command rather than manually editing a hundred and fifty files? Thanks....

---

### Post by BoneKracker on 2010-06-02
Does ROBOTNAME from one file also appear in the other files (where it should not be changed)?  If not, it should be pretty easy.

Something like:
```
sed -s -i.bak "/$ROBOTNAME/ s/gif/png/" *.html
```

Create a loop (or similar mechanism) to pass each ROBOTNAME in sequence to that.  You could read each ROBOTNAME from a file or something.

That sed expression will edit the files in place, creating filename.bak for each.  Note the use of double quotes.  The $ROBOTNAME variable won't work if you use single-quotes as shown in most sed examples.

---

### Post by rebeltaz on 2010-06-02
Aye aye aye! I might as well just do it manually if I have to create a name list... Thanks though.

---

### Post by BoneKracker on 2010-06-02
> **rebeltaz said:**
> Aye aye aye! I might as well just do it manually if I have to create a name list... Thanks though.

Well, you can't expect something to change the lines having those names in them if you don't tell it the names.

Let me ask you this though:

Can you uniquely identify the lines that need to be changed, in any way other than the actual ROBOTNAME?

If you can come up with a regular expression that isolates just the lines you want to change, then this is easy (even easier than above, because you wouldn't need a loop or a list of names).  I assumed you couldn't, because you said there were other lines indicating gif files, and I assumed them to be of identical format.  If you can, then you're home free.

Is there something that is always different between the lines you want to change and the other similar lines that you don't want to change, other than the fact that one includes a ROBOTNAME and the other doesn't?

---

### Post by rebeltaz on 2010-06-02
On the lines that I want to change, the filename always starts with 'images/robopix/web/' whereas the other gif files do not (they may be 'images/' or 'images/books/' or something like that). 

I was hoping for something along the lines of:

replace images/robopix/web/*.gif images/robopix/web/*.png

with * being a DOS-type wildcard.

---

### Post by BoneKracker on 2010-06-02
> **rebeltaz said:**
> On the lines that I want to change, the filename always starts with 'images/robopix/web/' whereas the other gif files do not (they may be 'images/' or 'images/books/' or something like that). 

I was hoping for something along the lines of:

replace images/robopix/web/*.gif images/robopix/web/*.png

with * being a DOS-type wildcard.

Yes, that's the idea.  Renaming files is actually even easier than that, but editing the contents of files is slightly more complex.

This ought to do it:
```

sed -s -i.bak '/robopix/ s/gif/png/' *.html
```

Okay, here's a walk-thru you can use to confirm if this will do what you need.  If any of this isn't right, it probably be fixed.

_Pattern:_ In sed, that part between the first pair of / / (where "robopix" is now, and where $ROBOTNAME was before, is the "pattern" used to select which lines are going to get changed.  If it sees a line that matches the "pattern", then it will try to do what's next (the "action", which in this case is "s/gif/png/").  In this case, we're now using a very simple pattern.  It's going to look for any line that contains the string "robopix" and attempt to carry out the action on it.  Because the pattern no longer includes a shell variable ($ROBOTNAME), the double-quotes can go back to being single-quotes, which are a bit safer because they prevent the shell from altering anything inside the sed expression.

_Action:_ The action is also a simple one.  It's going to substitute the string "png" for the first occurrence of the string "gif" that it finds.
[U]
Files:[/U] The last part is where a file or list of files goes.  In this case, I've assumed you have all these html files in one directory and used *.html.

Finally, if you don't want it to make backups, you can change the -i option to -i''
but that is not recommended, because an error halfway through the task can leave you in a messed up state.

---

### Post by rebeltaz on 2010-06-03
That worked great. Thank you for both the command an dthe time to explain it. One question, though. Why did you use the -s switch? I looked at the sed man page and it says that that treats each file as a separate entity instead of one continuous stream. Whenever I have used sed to do search-and-replace operations over multiple files, I've never used the -s switch and so far the results where always what I expected. Is there a specific reason to use it?

Thanks again...

---

### Post by BoneKracker on 2010-06-03
> **rebeltaz said:**
> That worked great. Thank you for both the command an dthe time to explain it. One question, though. Why did you use the -s switch? I looked at the sed man page and it says that that treats each file as a separate entity instead of one continuous stream. Whenever I have used sed to do search-and-replace operations over multiple files, I've never used the -s switch and so far the results where always what I expected. Is there a specific reason to use it?

Thanks again...

No, I have just always used it when editing multiple files in place -- I thought it was necessary. :lol:

Apparently it's not.

---

### Post by rebeltaz on 2010-06-03
> **BoneKracker said:**
> No, I have just always used it when editing multiple files in place -- I thought it was necessary. :lol:

Apparently it's not.

Oh no... don't go by me. It may have consequences that I haven't noticed.

---

