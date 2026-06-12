---
title: "I need to view a Windows .zip file."
date: 2005-03-06
forum: General Help
---

### Post by RU63 on 2005-03-06
For a project i was only given the option of downloading a Windows .zip file.

How can i get to use this file.  I assume I can do this in Wine... but I have never used wine.  

Thanks,

---

### Post by doitashimashite on 2005-03-06
You don't need Wine for that. Just right click on the ZIP file, and click "Extract here".

---

### Post by RU63 on 2005-03-06
ARG>>.  it isn't at zip file.. 

It is an exe file

lexiWin_zip.exe

Hoe do i view this?

---

### Post by kassetra on 2005-03-06
[QUOTE=RU63]ARG>>.  it isn't at zip file.. 

It is an exe file

lexiWin_zip.exe

Hoe do i view this?[/QUOTE]

That's a self-extracting zip file that you'll either have to use windows or wine to open.  If you want to use wine, you'll need to install it first.  Do you know how to use Synaptic?

---

### Post by poofyhairguy on 2005-03-06
[QUOTE=RU63]ARG>>.  it isn't at zip file.. 

It is an exe file

lexiWin_zip.exe

Hoe do i view this?[/QUOTE]

Two options:

Install wine. Run in wine. Pray that it works.

OR

Use some else's Winders box.

---

### Post by doitashimashite on 2005-03-06
No you still don't need Wine. Just use unzip.

$ man unzip:

" ... Note that self-extracting ZIP files are supported, as with any other ZIP archive; just  specify  the .exe suffix (if any) explicitly."

---

### Post by defiant on 2005-03-06
Try this:

unzip -l filename.exe

replace filename.exe with your file.

This should list the contents of the zip if unzip is able to view and manipulate contents.  If this is successful, try renaming the file to add a .zip suffix and gnomes gui interface may be able to decompress if for you.

have fun.

---

### Post by kassetra on 2005-03-06
[QUOTE=defiant]Try this:

unzip -l filename.exe

replace filename.exe with your file.

This should list the contents of the zip if unzip is able to view and manipulate contents. If this is successful, try renaming the file to add a .zip suffix and gnomes gui interface may be able to decompress if for you.

have fun.[/QUOTE]

I'm trying this now myself, because that's COOL if it works with self-extracting zips!  I haven't previously ever been able to open self-extracting zips, but it could be that I was using an older version of unzip (or too reliant upon the gui).

Learn something new everyday!  Thank your for such an awesome tip defiant!  :)

---

### Post by kassetra on 2005-03-06
[QUOTE=doitashimashite]No you still don't need Wine. Just use unzip.

$ man unzip:

" ... Note that self-extracting ZIP files are supported, as with any other ZIP archive; just specify the .exe suffix (if any) explicitly."[/QUOTE]

man.  I must be stuck in the unzip dark ages.  Now I know though.  That is so cool.

---

### Post by lordofkhemenu on 2005-03-06
[QUOTE=kassetra]man.  I must be stuck in the unzip dark ages.  Now I know though.  That is so cool.[/QUOTE]
We have to be careful, those guys shining the bright lights are gonna make us in the dark ages go blind!
I was in the same boat as you, I had ***NO*** idea about the .exe thing either.
Schweet. I can finally tell my brother to wipe that smug look off of his face.:mrgreen:

---

