---
title: "Ubuntu filesystem"
date: 2009-10-13
forum: General Help
---

### Post by KommerszUnicum on 2009-10-13
Hi Guys!

I'm trying to learn a little about the Ubuntu/Linux, but I've stucked with the filesystem. In W*nd*ws a program in the filesystem can be located easily because the most part will be put in a directory which we want to choose during the install. But in linux the directory structure is not very clean for me. The package installer uses a lot of directory everywhere to put the packege files into the system. Is Ubuntu using a "standard" way to copy the file together? As I can see there are a lot of other stuff in a specified directory like for example lib not just library files. Why is it necessary for the linux to create /opt/usr for user files instead of using the /usr? Could you suggest me a useful guide which can help me understand the filesystem and get answers all of my question about the filesystem hierachy (especially for ubuntu "standard")??

Thank you for your help!
KommerszUnicum

---

### Post by wojox on 2009-10-13
Here's a good site: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by KommerszUnicum on 2009-10-13
Thank you! It seems very useful!

---

### Post by Lars Noodén on 2009-10-13
Also the specific layout for Ubuntu, which should closely match FHS that @ wojox  mentioned, would be found in the manual page [hier(7)](http://manpages.ubuntu.com/manpages/jaunty/en/man7/hier.7.html)

---

### Post by Penguin Guy on 2009-10-13
> **Lars Noodén said:**
> Also the specific layout for Ubuntu, which should closely match FHS that @ wojox  mentioned, would be found in the manual page [hier(7)](http://manpages.ubuntu.com/manpages/jaunty/en/man7/hier.7.html)
I believe what he means is that all the information you want is in the [COLOR="Green"]hier[/COLOR]archy manpage, which you can view by opening the terminal and running:
```
man hier
```
or you can put it in a text file using:
```
man hier >"$HOME/Desktop/Hierarchy Manpage"
```

---

### Post by vinutux on 2009-10-13
check this link [http://www.google.co.in/url?q=http://en.wikipedia.org/wiki/File_system%23File_systems_under_Linux&usg=AFQjCNE-_HeHU-lpS3MBaPo7z83e1QxtsQ&ei=19rUSuPAFZjU6gOU9pHnCw&sa=X&oi=section_link&resnum=1&ct=legacy&ved=0CBAQygQ]("http://www.google.co.in/url?q=http://en.wikipedia.org/wiki/File_system%23File_systems_under_Linux&usg=AFQjCNE-_HeHU-lpS3MBaPo7z83e1QxtsQ&ei=19rUSuPAFZjU6gOU9pHnCw&sa=X&oi=section_link&resnum=1&ct=legacy&ved=0CBAQygQ")

---

### Post by KommerszUnicum on 2009-10-13
Thank you Guys!

---

### Post by Lars Noodén on 2009-10-14
> **Penguin Guy said:**
> 
or you can put it in a text file using:
```
man hier >"$HOME/Desktop/Hierarchy Manpage"
```

Or you can use man2html and view it as a web page on your own machine.  Or you can look at someone else's web server manual page for [hier](http://manpages.ubuntu.com/manpages/jaunty/en/man7/hier.7.html) ;)

The tool 'locate' is useful, too.

---

