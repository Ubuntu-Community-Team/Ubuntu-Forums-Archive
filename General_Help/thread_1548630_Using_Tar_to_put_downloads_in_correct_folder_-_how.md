---
title: "Using Tar to put downloads in correct folder - how?"
date: 2010-08-08
forum: General Help
---

### Post by zozza on 2010-08-08
If I download a .deb file then when I run dpkg all files install in the  correct directories.

But with a tar.bz2 file when I run tar xvjf  it installs in its current directory.  

How can I make a tar.bz2  file install into the appropriate directory?

Thanks.

---

### Post by AlphaLexman on 2010-08-08
The application 'alien' can convert different 'distro' packages to another format.

However many '.tar.bz2' packages are actually 'source' files and need to be compiled first.

The standard compile input is:
```
./configure
make
install

```
You would run these commands after you 'un-bzipped' the downloaded file. But check the README file included with the compressed file.

---

### Post by luigi_mb on 2010-08-08
You can see the file tree structure by executing

```

$ tar -tvf filename.tar.gz | less

```

As AlphaLexman says, most of these archives contain source code, which needs to be compiled. In many, if not most, cases this will install the files in the appropriate locations:

```

$ tar -xvf filename.tar.gz
$ cd .... # to the folder created in the line above
$ ./configure
$ make
$ sudo make install

```

In any case, after unpacking the archive, read README (sometimes README.txt) and INSTALL for detailed instructions, and requirements/dependencies.

/luigi

---

### Post by bodhi.zazen on 2010-08-08
> **zozza said:**
> If I download a .deb file then when I run dpkg all files install in the  correct directories.

But with a tar.bz2 file when I run tar xvjf  it installs in its current directory.  

How can I make a tar.bz2  file install into the appropriate directory?

Thanks.

This is because of how .deb are packaged.

If you want the gory details, see 

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

With tar it is best to read the command line. It depends on exactly how the archive was made.

When you extract an archive , it extracts the contents into the current directory. Most people cd then extract

cd / 
tar ....

But you can use the -C option

tar xvf foo.tar -C /

See 

[http://www.geekvenue.net/chucktips/jason/chuck/994016279/index_html](http://www.geekvenue.net/chucktips/jason/chuck/994016279/index_html)

And man tar

[http://manpages.ubuntu.com/manpages/lucid/man1/tar.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/tar.1.html)

---

### Post by zozza on 2010-08-09
Thanks for all the advice.  In this case I am using thunderbird.tar.bz2 which, I understand, is different from "normal" files of this nature, because I do not need to compile. 

I copied the .tar.bz2 file into /usr/lib after deleting the older thunderbird directory and untarred it which made /usr/lib/thunderbird

Then I used PATH=$PATH:/usr/lib/thunderbird

This works fine - however I wonder in which file/s these PATH commands are stored?

Thanks.

---

### Post by bodhi.zazen on 2010-08-09
You set a path in ~/.bashrc

Add (or edit) this line :

```
export PATH=$PATH:/usr/lib/thunderbird
```

---

### Post by zozza on 2010-08-09
I did try that in .bashrc but it does not work.

What works is typing this into the console:

PATH=$PATH:/usr/lib/thunderbird

For some reason this allows thunderbird to be accessed from any directory.

Any ideas why?

---

### Post by bodhi.zazen on 2010-08-09
> **zozza said:**
> I did try that in .bashrc but it does not work.

What works is typing this into the console:

PATH=$PATH:/usr/lib/thunderbird

For some reason this allows thunderbird to be accessed from any directory.

Any ideas why?

After adding that to .bashrc you need to start a new shell, source .bashrc, or better log off and back in.

If it does not work, probably a typo.

---

