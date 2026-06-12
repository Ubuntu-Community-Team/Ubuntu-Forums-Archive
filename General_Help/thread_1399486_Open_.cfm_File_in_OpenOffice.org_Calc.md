---
title: "Open .cfm File in OpenOffice.org Calc?"
date: 2010-02-05
forum: General Help
---

### Post by jrolland on 2010-02-05
Hello, all!

I am a teaching assistant at a university. My university posts class rosters in a supposed MS Excel format, which is secretly a .cfm (Cold Fusion, a web-type file, I think - I'm not super-familiar with the file format, but when I cracked the file open in a text editor, it appeared to be an html table) file.

I used to use MS Excel for Mac, and it opened this file happily.

Now, I have switched to Ubuntu for PC at my office, and I can't get the file to open in OpenOffice.org Calc.

The file will *sorta* open in OpenOffice.org Writer, but not completely: part of the main table containing the student's data, the part of the table "to the right side" of where the page cuts off, is cut off.

"Smokey" Ardisson has written a neat NeoOffice Applescript, TSV Helper (<http://www.ardisson.org/smokey/mac/index.html>), that tells NeoOffice to open any file formats you tell it to open (.tsv, .csv, .cfm, etc.) in NeoOffice Calc - i.e., NOT NeoOffice Writer.

I have tried emulating the Applescript to tell OpenOffice.org to try directly opening the file in Calc, but it just fails to open the file entirely.

I have tried this under both Ubuntu Hardy (at school) and Ubuntu Intrepid (at home) - no love.

Can anyone give me a whizz-bang solution to open .cfm files directly in OpenOffice.org Calc? Many thanks in advance.

---

### Post by Leppie on 2010-02-05
if this is supposedly a web format, have you tried opening it in a browser?

---

### Post by gmargo on 2010-02-05
> **jrolland said:**
> Can anyone give me a whizz-bang solution to open .cfm files directly in OpenOffice.org Calc?

Can you give us a pointer to a whizz-bang .cfm file?

---

### Post by Leppie on 2010-02-05
> **gmargo said:**
> Can you give us a pointer to a whizz-bang .cfm file?
there's actually quite a lot of cfm web pages.

---

### Post by jrolland on 2010-02-06
> **gmargo said:**
> Can you give us a pointer to a whizz-bang .cfm file?

Actually, as I said, the actual files produced are student-information files, so I can't post them.

I'll take a shot at manually editing one them with gobbley-gook data, but I can't promise I won't accidentally mangle it in the process.

---

### Post by jrolland on 2010-02-06
> **Leppie said:**
> if this is supposedly a web format, have you tried opening it in a browser?

Sure, but the problem is I need the information in Calc (in neat little columns-and-rows) so I can use the data to keep track of my students' grades.

---

### Post by jrolland on 2010-02-06
> **jrolland said:**
> Actually, as I said, the actual files produced are student-information files, so I can't post them.

I'll take a shot at manually editing one them with gobbley-gook data, but I can't promise I won't accidentally mangle it in the process.

OK, here's one I "mocked up". It opened fine in NeoOffice TSV Helper, so I don't think I mangled it (too badly), but YMMV.

Thanks again in advance for any assistance you can provide.

---

### Post by Leppie on 2010-02-06
i'm not installing openoffice to see how it opens in its calc.
i just opened it in gnumeric and works like a charm, you may want to try using that instead of hurting your brain and try to open it with openoffice's calc.

edit: i attached a screenshot

---

### Post by jrolland on 2010-02-06
> **Leppie said:**
> i'm not installing openoffice to see how it opens in its calc.
i just opened it in gnumeric and works like a charm, you may want to try using that instead of hurting your brain and try to open it with openoffice's calc.

edit: i attached a screenshot

OK, I'll try gnumeric, but I'd still appreciate if someone can come up with an OpenPffice.org Calc solution.

Thanks again!

---

### Post by Leppie on 2010-02-06
> **jrolland said:**
> OK, I'll try gnumeric, but I'd still appreciate if someone can come up with an OpenPffice.org Calc solution.

Thanks again!
i get the same result in openoffice calc. just right click the file and select "Open With" then "Open With Other Application..." then "OpenOffice.org Spreadsheet". if you select the "Use as default for this kind of file" all .cfm files will open using openoffice calc.

---

### Post by jrolland on 2010-02-06
> **Leppie said:**
> i get the same result in openoffice calc. just right click the file and select "Open With" then "Open With Other Application..." then "OpenOffice.org Spreadsheet". if you select the "Use as default for this kind of file" all .cfm files will open using openoffice calc.

Yeah, that just started working for me, too. I had tried using the command line command "openoffice.org -calc index.cfm", and that just produced nothing. I'm not sure if I tried the "Open With" GUI command. I just looked in the menus, and it appears I should have been using the command line command "openoffice.org3 -calc index.cfm"; that works like a charm.

OK, thanks a lot for all the help, is really appreciated. It really ircs me when there isn't a FOSS alternative to doing things one can do on Windows (or Mac OS X), so I'm really glad this worked out, and worked out so easily. I'll mark this thread "SOLVED".

Addendum: Actually, I found out what the problem was. On my Intrepid box at home, I had followed the instructions on [http://www.ubuntu-inside.me/2009/05/openoffice-31-for-ubuntu.html]("http://www.ubuntu-inside.me/2009/05/openoffice-31-for-ubuntu.html") in the hopes of keeping up-to-date on OpenOffice.org, but it only installed version 3.1.0. I followed the instructions on [http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04]("http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04"), changing to download the .debs for version 3.1.1, and OpenOffice.org Calc opened the .cfm file like a champ. (Actually, I tried to open the .cfm file the first time I opened version 3.1.1, but the first time opening OpenOffice.org, it like to set your name and ask you to register, so it crashed; this sent me into an infinite loop of crash recoveries, providing a half-hour of joy until I renamed my OpenOffice.org directory from ~/.openoffice.org to ./openoffice.org.backup, launched OpenOffice.org once to set my name and register, a second time to decline providing anonymous data, and a third time to open the .cfm file.) So, it's really version 3.1.1 that provides the .cfm file functionality.

Thanks again, it's forums like this that really make Ubuntu work, IMHO.

---

### Post by Leppie on 2010-02-06
glad it's working for you as well now :)
we're here to help each other out ;)

---

