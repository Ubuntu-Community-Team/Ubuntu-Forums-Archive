---
title: "cannot find downloaded iso image"
date: 2011-04-10
forum: General Help
---

### Post by Sea Otter on 2011-04-10
Hi, I just downloaded an ISO image to my Ubuntu laptop. I did the mistake in Firefox to just select the default method of "Open with - Archievmanager (default)" and now I cannot find the files (or if it has split up in a lot of files) Can anybody help me here?
Thanks, Chris

---

### Post by TeoBigusGeekus on 2011-04-10
It is somewhere in your home folder, inside firefox's temp folder or something (I don't use firefox, can't say which is its name).
You can do a 
```
find ~/ -name "*.iso" 2>/dev/null
```
to find it.

---

### Post by drewsus on 2011-04-10
You could also use "Search for Files" in **Places**.

Or, open your browser download manager/list and right-click on the downloaded file and say open in directory.

---

### Post by Sea Otter on 2011-04-10
> **drewsus said:**
> You could also use "Search for Files" in **Places**.

Or, open your browser download manager/list and right-click on the downloaded file and say open in directory.

I already tried that but the two buttons on top in that window is greyed out and no possibility to select. I did the download again and this time saved as it should be, this time I could find the file with just doing as you said.

The first download is not to be found. I just hope they will not disturb the system somehow.

all the best,

Chris

---

### Post by drewsus on 2011-04-10
If you do the search for files option that I mentioned, use the search term: "*.iso" (without the quotation marks) and you should be able to find where any stray ones are. The asterisk is a wild card.

---

### Post by tredegar on 2011-04-10
> The first download is not to be found. I just hope they will not disturb the system somehow.

If you chose "Open with - Archievmanager (default)" then that is what it will have done. If you did not then extract the files somewhere and you have closed the "Archive manager" window, they are probably already gone from **/tmp/** if not, they will be when you next logout.

So, don't worry about it.

---

### Post by Sea Otter on 2011-04-10
> **tredegar said:**
> If you chose "Open with - Archievmanager (default)" then that is what it will have done. If you did not then extract the files somewhere and you have closed the "Archive manager" window, they are probably already gone from **/tmp/** if not, they will be when you next logout.

So, don't worry about it.

Sounds good, I was worried a while. Thanks Tredegar.

Now I just need to get the USB devices going when using Virtual Box, but more of that in a more correct thread I started.

All the best,

Chris

---

### Post by d3v1150m471c on 2011-04-10
```

locate .iso | grep -i "part of the iso's name"

```

---

