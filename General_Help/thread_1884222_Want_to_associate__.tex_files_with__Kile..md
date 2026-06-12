---
title: "Want to associate  .tex files with  Kile."
date: 2011-11-20
forum: General Help
---

### Post by Randy Schilling on 2011-11-20
I'm trying to associate my TeX file with Kile.
But Kile is not presented as an option.
Its in my /usr/bin folder along with Kate and Kate is presented as an option.
What do I have to do?

---

### Post by hwttdz on 2011-11-21
I think you just right click a .tex file, and go to properties, select open with (might be a tab), and if the program you want is not listed, pick "use custom command" and then give the path to the program you want.

---

### Post by Randy Schilling on 2011-11-21
I've done exactly what you describe...to a point.
There  is no "use custom command"; instead,
clicking "Show other application" gives a long list which does NOT include Kile.
The Reset button does not help; i.e., it doesn't add Kile to the list.
The discussion under the Help button does not address this issue.
I checked that the executables for both Kile and Kate are located in /usr/bin;
their permissions are identical.

Oddly, Kile IS presented as an option when you menu-click a .tex file 
and then click "Open with" (instead of Properties).  
This approach however does not allow you to select a default application.

Kile is a very good editor, arguably the best that Linux provides, for .tex files.
I'm reading now through Kile's setup documentation for help with this issue.


Thanks so much for taking time with my problem - Randy

What does it mean to "pm you?"

---

### Post by Vaphell on 2011-11-21
look at kile.desktop file in /usr/share/applications
probably it's not listed to show in gnome/unity environments

another possibility is to use something else, maybe geany+latex plugin (geany and geany-plugins packages)?

---

### Post by Randy Schilling on 2011-11-21
Vaphell:

/usr/share/applications contains files of type "desktop configuration files".
It also contains a subfolder, kde4, which contains a desktop configuration file named Kile.
But I still don't know what to do to add an entry "Kile" to the list of options displayed under  "Open with" > "Show other application".
Please explain.

Oh yes.  I'm trying several editors for TeX (TeXMaker, TexWorks, Kile,...,
all (except Kile) appeared automatically among the options displayed under  "Open with" > "Show other application".).  
I've used WinEdt for years but it's strictly Windows.
TeXmaker is very nice but it's setup strictly for LaTeX.  
I've been a TeX user for many years so I have to check to see if TeXMaker can be configured for TeX.
All editors so far, except Kile, lack one thing or another, in my opinion.
I'll add geany to my list of editors to look at.

Dzi&#281;kuj&#281;, from someone of Polish ancestry living in Arkansas, United States. - Randy

---

### Post by Vaphell on 2011-11-21
so i did a test in virtualbox
who thought it was a great idea to not allow for file associations with custom apps in 11.10? o.O

i managed to get this working, i opened /usr/share/applications/defaults.list and added the following line:
```
text/x-tex=kile.desktop
```
after logout/login i get kile listed as default and gedit is in 'suggested' group. Doubleclick on .tex opens kile.

---

### Post by mc4man on 2011-11-22
(**if you are using gnome3**
In gnome3  when apps that show on the right click 'open with' context menu but not on the r. click Properties menu do so because the Exec= line in the apps .desktop doesn't end with a %<letter>

That's the case with kile. The 2 most likely letters would be f or U, I'd try U first.

```
gksudo gedit /usr/share/applications/kde4/kile.desktop
```

Make the Exec= line look like this
```
Exec=kile %U
```

Save (close out that annoying 'untitled document' without saving

Should then show (do a log out/in if needed

---

### Post by Randy Schilling on 2011-11-22
Yes, U works! Thanks.

---

### Post by whosane21 on 2011-12-18
> **mc4man said:**
> (**if you are using gnome3**
In gnome3  when apps that show on the right click 'open with' context menu but not on the r. click Properties menu do so because the Exec= line in the apps .desktop doesn't end with a %<letter>

That's the case with kile. The 2 most likely letters would be f or U, I'd try U first.

```
gksudo gedit /usr/share/applications/kde4/kile.desktop
```

Make the Exec= line look like this
```
Exec=kile %U
```

Save (close out that annoying 'untitled document' without saving

Should then show (do a log out/in if needed



I had the same problem with Unity on Ubuntu 11.10.  This trick perfectly solved the problem and let me open .tex files with Kile by default.  Thanks!!

---

### Post by steveredshaw on 2011-12-27
can I do similar to associate .md files with MoneyDance (please give simple instructions as CLI is still fairly unknown territory)

I am using gnome3 and unlike previous versions there does not appear to be a GUI way of using a custom command or exploring the computer to get a particular file associated with its program if that program does not appear in the given list of applications

my MoneyDance (which is a Java application) is within a folder named programs within my home folder - there is perhaps a more sensible/appropriate place for it?

thanks...

---

### Post by agustingarcia8 on 2012-07-30
Dear all, 

I have a similar problem. Kile did not appear in my Ubuntu 11.10 as an option in "select another application" and now it does thanks to your advice. Nevertheless, it did appear (and still does) as a second option when I right clicked a tex file. The question is: how do I settle kile as the default program to open tex files? 

Thank you very much.
Agustín.

---

