---
title: "Problems with &quot;Open With&quot; in Nautilus"
date: 2006-05-11
forum: General Help
---

### Post by Scanner on 2006-05-11
Okay I know I have seen this before but have been searching for about an hour and cannot find the solution. 

When I right click on a file in Nautilus I get an option to open With Another Application.   This brings up a dialog qwith all my installed applications and I should be able to choose the one I want to use to open the file, I choose one and then get the error message:

Could not add application to the application database

I know that this is just a file permission error, but for the life of me I cannot remember the name and or location of the file that need to be fixed.

Where this usually gets me and an even better fix is to figure out where the default text editor is set so I can change taht to GVIM instead of GEdit

Thanks in advance.

---

### Post by Ramses de Norre on 2006-05-11
```
sudo update-alternatives --config editor
```

Things like gedit opening files are set with the open with tab in the preferences of such a file in nautilus.

If there's a way to make double clicking a text file in nautilus open it in vi, tell me!

---

### Post by xenmax on 2006-12-13
>  If there's a way to make double clicking a text file in nautilus open it in vi, tell me!I was looking for a solution to same question when i found this in search results.

Its a little late, but may help others who might stumble upon this thread - I have found a way to do this.

Open the alacarte menu editor - Applications->Accessories->Alcarte Menu Editor
Click on Accessories on left side of window, which displays all menu items under this on the right side. Right click on *Text Editor* entry and select *Properties *which opens an entry editor where command for editor can be specified. By default it is gedit, you can change it to editor of your choice like gvim (or specify full path)

Hope this helps.

---

