---
title: "weblinks"
date: 2010-07-02
forum: General Help
---

### Post by tuppence on 2010-07-02
Hi..!! 
I wonder if someone could help please... as I can't find a soulution to this weird problem..!!

Since opening a Zip file from a friend (text and pictures
of which i could only see pictures and all text was html enclosed) all
my weblinks on my desktop come up in html., in what looks like the text
editor. So i can't get the website concerned.
The weblinks on my panel are not affected nor weblinks in other
doc.files, it seems. 
So only links added to desktop.


Is it possible i that i have done something with my setting when accessing the zip file..?

I've looked around for file settings /anything that resembles .. but can't find solution or have missed it .. links in panel are ok ..

many thanks in advance..

sarah

---

### Post by philinux on 2010-07-02
Right click on one of you weblinks on desktop. Click on properties and then Open with other application and choose Firefox.

---

### Post by WorMzy on 2010-07-02
If you want them to open in a web browser, right click one, choose properties, click on the "Open With" tab, and select the browser of your choice from the list. If the browser you want isn't there, then click add, and choose one from the list. If you still don't see the browser you want to use, then enter a custom command to launch the program.

When you're done, just click close, and all the files of that type will now open in the browser.

---

### Post by tuppence on 2010-07-02
thank you both of you ..!! i have done this but no result.  when i Right clik the link icon, then Properties the sitelink properties do come up in menu, but  only with Basic,Emblems,Permissions,Notes tabs. Nothing there resembles what you say.
 I do know what you refer to as i have seen an 'open with' option, but it is not there.

sarah

---

### Post by WorMzy on 2010-07-02
That's strange. Do you get the Open With tab if you open the properties of other files?

Can you drag one of the weblinks into Firefox (or another browser)?

Finally, can you open a terminal, cd to the directory where the weblinks are currently stored, and run ```
file <filename>
``` on one of them, then post the output here.

---

### Post by tuppence on 2010-07-02
thank you ..!! yes, when i open other files  i get the 'open with' tab.  and yes i can drag the weblikk icon into FFox.WebBr. and the site come up. 
dragging different sites into browser changes the site correctly but doesn't give a tab to get the previous site back again.

i dont understand the final thing you mention, about open a terminal, (although i am aware  there is  a terminal in Applications,Accessories,Terminal.  
do you mean that?)  or the rest of what you say.

sarah

---

### Post by WorMzy on 2010-07-02
Yes, if you open that terminal (Applications -> Accessories -> Terminal), and use it to browse to the location of the files (e.g. if they're in your Downloads folder, type 'cd ~/Downloads', and hit enter), then run the command 'file <filename>' (e.g. 'file a-website.html'), it'll display some information about what the file is. If you copy that information and paste it here, it might tell us why it's not showing the Open With tab in it's properties. From there we might be able to tell you how to proceed.

---

### Post by tuppence on 2010-07-02
i opened a terminal and typed in  as you say .. this is the result..below.. 
have i done it correctly? It was a blank terminal with  my name on it..  
i am not familiar with this..

sarah@ubuntu:~$ cd~/Downloads
bash: cd~/Downloads: No such file or directory
sarah@ubuntu:~$ filehttp://www.exchangeandmart.co.uk
bash: filehttp://www.exchangeandmart.co.uk: No such file or directory
sarah@ubuntu:~$

---

### Post by WorMzy on 2010-07-02
You need a space between the command and the file/folder name. But let's forget about that for now.

Instead, can you browse (in the file browser) to where the files are and take a screenshot of the files you're trying to open? Attach it to your post by clicking the little paperclip in the reply window, or upload it to an image hoster (such as [Imageshack]("http://imageshack.us/")) then post the link here.

---

### Post by tuppence on 2010-07-02
it just says invalid file when i have uploaded it .. so it wont attach.!  all the file is   is html.. as if it were written in  a text editor.

---

### Post by WorMzy on 2010-07-02
Okay. Press Alt+F2 and run this command exactly as I've written it (copy and paste it if necessary)

```
[COLOR="DarkGreen"]gksu gedit /usr/share/applications/defaults.list[/COLOR]
```

It'll prompt you for your password, enter it, then press enter.

You'll get a text editor with a lot of lines in it. Press Ctrl+F to bring up the search box, and enter:```
application/xhtml+xml
``` press enter or click the Find button. If it can't find it, then don't worry. If it does, change the end of the line it found so that the whole line says:
```
[COLOR="Red"]application/xhtml+xml=firefox.desktop[/COLOR]
```
Next, press Ctrl+F again, and this time search for:
```
text/html
```
Again, don't worry if it's not found, but if it is, edit the line so it says:
```
[COLOR="Red"]text/html=firefox.desktop[/COLOR]
```


Now, if you couldn't find one or more of these lines, then add them to the bottom of the file.

Next, save and close the file. Then press Alt+F2 again, and this time run:```
[COLOR="DarkGreen"]gksu gedit /usr/share/applications/mimeinfo.cache[/COLOR]
```

Once again, search for
```
application/xhtml+xml
``` and change the whole line so it says ```
[COLOR="Red"]application/xhtml+xml=firefox.desktop;[/COLOR]
```
Then search for
```
text/html
```
and change the whole line so it says:
```
[COLOR="Red"]text/html=firefox.desktop;[/COLOR]
```

Again, if either of these lines don't exist, then add them to the bottom of the file. Save, logout, and log back in, and you should now be able to open the files in Firefox by default.

---

### Post by tuppence on 2010-07-02
many thanks WorMzy..!!  i will do this in the morning when i have more time to concentrate on it.  :)  and let you know.

---

### Post by tuppence on 2010-07-03
Hi ..!! i have done this sequence .. but still  links come up in 
editor as html..!!!?
all the code lines were in there as you had written..
sarah

---

### Post by WorMzy on 2010-07-03
I'm sorry that didn't work, but I have no other suggestions.

Hopefully someone else will be able to offer some better advice. :)

---

### Post by tuppence on 2010-07-03
well.. thank you very much for being so helpfull.. i have given it another go and still no luck.. what puzzles me is that everything was ok till i  opened the zip file i recieved.. and still more is that any links on panel are ok  too..  anyway i'm not around for a few weeks now so maybe i can  post in again  later to see if anyone else can help .. and will keep this thread.. maybe also you may think of something..!  many thanks again..!!
sarah

---

