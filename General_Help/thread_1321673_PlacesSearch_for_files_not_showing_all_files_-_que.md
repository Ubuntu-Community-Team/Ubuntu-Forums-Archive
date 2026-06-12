---
title: "Places/Search for files not showing all files - question"
date: 2009-11-10
forum: General Help
---

### Post by notgoingbackto_ms on 2009-11-10
I searched for a specific file that I had downloaded using the Places/Search for files app, but it did not find the file. I drilled to the file using Places/Computer/Filesystem and went directly to the Home/xxxxxxxx folder and discovered that many more files are listed here vs using Places/Search for files. Is there a reason for this or is something broken? The app can only find a small subset of what actually exists there.



9.10

---

### Post by hal8000 on 2009-11-10
> **notgoingbackto_ms said:**
> I searched for a specific file that I had downloaded using the Places/Search for files app, but it did not find the file. I drilled to the file using Places/Computer/Filesystem and went directly to the Home/xxxxxxxx folder and discovered that many more files are listed here vs using Places/Search for files. Is there a reason for this or is something broken? The app can only find a small subset of what actually exists there.

9.10

If I understand you, you tried to use the menu Paces, Search for files, but could locate what you were searching for. However when browsing file system you found your file.

The search for file option looks for a specific file or file descriptor.
If you were to type wildcard * in the name contains dialog, then it would search for all filename and recursively through folders.

You also have options to search for a string of text within a file, so its quite versatile, but wont search for hidden files starting with "."


There is nothing wrong wiith it and works fine on karmic. What you haven't told us is what you looked for. Also remember that it starts looking by default in /home/username  not /home so this is proberbly where you went wrong.
If your file is located in /home then you need to click filesystem then /home to begin your search *jpg for example looks just for jpg's
though there is nothing wrong with the unix find command in my opinion.
Hope that helps.

---

### Post by notgoingbackto_ms on 2009-11-10
It helps somewhat. Thanks

I have the search app  set to File System, and can find some of the files listed in the /home/xxxxxxxx folder - example, I can find the Pictures folder - no problem. When I scroll down further I see a file called .bash-history (using the File Browse app), but the find-app will not located it  - even with the hidden option set there - that does not make sense.

---

### Post by tekstr1der on 2009-11-10
Try searching for bash_history as that is the filename I think you are referring to.

---

### Post by hal8000 on 2009-11-10
> **notgoingbackto_ms said:**
> It helps somewhat. Thanks

I have the search app  set to File System, and can find some of the files listed in the /home/xxxxxxxx folder - example, I can find the Pictures folder - no problem. When I scroll down further I see a file called .bash-history (using the File Browse app), but the find-app will not located it  - even with the hidden option set there - that does not make sense.

It did find the .googleearth folder.

I just tried search with hidden folders and it also did not display any hidden files/folders.
However theres a much quicker and easier way. Go to places home folder. Go to view and tick hidden files or (ctrl+H) you can now quickly navigate your home folder.

If its .googleearth then

sudo find /home -name .googleearth

is just as fast. 
Hope that helps

---

### Post by tekstr1der on 2009-11-10
> **hal8000 said:**
> I just tried search with hidden folders and it also did not display any hidden files/folders.
However theres a much quicker and easier way. Go to places home folder. Go to view and tick hidden files or (ctrl+H) you can now quickly navigate your home folder.

If its .googleearth then

sudo find /home -name .googleearth

is just as fast. 
Hope that helps

Are you using Places > Search for Files... ? This should provide identical results to the terminal find command as it's just a GUI front-end for the same.

---

