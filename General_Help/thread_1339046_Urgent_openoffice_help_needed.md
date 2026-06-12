---
title: "Urgent openoffice help needed"
date: 2009-11-27
forum: General Help
---

### Post by solomon88 on 2009-11-27
Hey so I think I have accidently messed up openoffice. I did something in the terminal to try and get openoffice to work with a darker theme. After I did this openoffice refuses to 
open. I have tried a complete reinstall which did not work and have tried opening it from the terminal using
[html]oowriter[/html]and i get the following message

[html]env: /usr/lib/openoffice/program/soffice2: Permission denied[/html]I really need to get this fixed asap, an essay due date is looming as as of now I cannot access it. Is there a good word processor that someone could recommend in the mean time? Cheers guys.

---

### Post by mdurham on 2009-11-27
create a new user and try from there, it might work!

---

### Post by HereInOz on 2009-11-27
Firstly, uninstall Open Office using Synaptic.

Then open up Nautilus in your Home folder, then press CTRL-H to show the hidden folders.  Delete all folders which start with .openoffice

Re-install Open Office.  It should work now.

---

### Post by HereInOz on 2009-11-27
Second thoughts, also open a terminal and run:

sudo rm -r /usr/lib/openoffice  (you may need a / on the end of that, not sure)  This should overcome your permission denied issue.

Alternatively try:

sudo su
(enter password)
ls -l /usr/lib/openoffice/program

and see what the permissions are on the soffice folder.  You may be able to change them with chmod, and get your Open Office back that way.  You would need at least read permissions for user, group and others, I would think.

---

### Post by solomon88 on 2009-11-27
Unfortunately neither of these options worked :(
I have no files beginning with .openoffice in my nautilus folder, so no joy there. 

I did put sudo rm -r /usr/lib/openoffice into the terminal (with and without /) and got the following response.
 [html]rm: cannot remove `/usr/lib/openoffice/': No such file or directory[/html]In regards to the third suggestion:
sudo su
(enter password)
ls -l /usr/lib/openoffice/program

After I put in sudo su the following appears
[html]root@matthew-laptop:/home/matthew#[/html]I was never prompted for a password. Though I suppose now you all know my name is Matthew and I am on a laptop, no biggie. 

I am sorry about all of this, I feel like this shoudnt be quite as hard as I am making it, though my growing level of frustration isnt helping. Any other suggestions? Cheers.

---

