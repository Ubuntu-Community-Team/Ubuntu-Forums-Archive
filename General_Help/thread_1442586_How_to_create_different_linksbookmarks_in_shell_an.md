---
title: "How to create different links/bookmarks in shell and Nautilus?"
date: 2010-03-30
forum: General Help
---

### Post by HotForLinux on 2010-03-30
If I want to make a link A in directory DIR-A to folder B, in directory DIR-B, I can do a soft link with a command line or I can do it in a file Manager.
Nautilus does not provide a comfortable and quick way to do it for all occasions because you need to go to DIR-B first, create a link to B there and then move the link to DIR-A.

The problem with th[COLOR=Red]ese[/COLOR] links is that when you access the link A, you see the contents of B but when you go up to the [COLOR=Red]parent[/COLOR] directory you are back in DIR-A which is sometimes not what you wanted.

You can also create a  ***.**desktop file (a launcher to a Location), to walk around this problem, in Nautilus ([COLOR=Blue]°[/COLOR]). But I think that these type of links are program dependent...Aren't they?

Moreover, this files can't be used as links in the shell.

Any ideas of how can this be achieved for the shell?


([COLOR=Blue]°[/COLOR]) Again, in my opinion, this is not very well done/explained in Nautilus and you can only do it by right clicking on the Desktop -why? or bookmarking B and dragging the bookmark to a gnome-panel and then from the panel  to DIR-A


P.D.
By the way, does anyone know a reason why soft links work in that way and do not take you completely to the destination?

---

### Post by ajgreeny on 2010-03-30
Actually, the quickest way with nautilus is to drag with the mouse middle button.  A mini-menu will appear asking if you want to move, copy or link.  Choose "link" and there you are; all done!

---

### Post by HotForLinux on 2010-03-30
> **ajgreeny said:**
> Actually, the quickest way with nautilus is to drag with the mouse middle button.  A mini-menu will appear asking if you want to move, copy or link.  Choose "link" and there you are; all done!

Or press the <Alt> key before releasing the mouse button and choose link. But that link will behave exactly the way I said I'm not interested. Not only in the graphic desktop environment but in the shell too.

I said:
> The problem with these links is that when you access the link A, you see the contents of B _but when you go up to the parent directory you are back in DIR-A_ which is sometimes not what you wanted.

---

### Post by HotForLinux on 2010-04-05
-bump-

---

### Post by HotForLinux on 2010-05-25
> **HotForLinux said:**
> 
...
Any ideas of how can this be achieved for the shell?
... 

Good news:

A few days ago I discovered how this can be done in the shell environment.

```

$man cd

NAME[INDENT] **cd - change the working directory**

 -L     Handle the operand dot-dot logically; symbolic  link  components shall  not  be  resolved before dot-dot components are processed (see steps 8. and 9. in the DESCRIPTION).

-P     Handle the operand dot-dot physically; symbolic link components shall  be  resolved before dot-dot components are processed (see step 7. in the DESCRIPTION).[/INDENT]
```And also, even if the man page in Ubuntu doesn't say _ANYTHING_ about it, the command pwd has the -P option to display either the present directory, where the link-directory is or the permanent directory, where the link points to.

```

$man pwd

NAME[INDENT] pwd - print name of current/working directory

 [COLOR=Red]- nothing explained here -[/COLOR] (will some one fix this???)
[/INDENT]
```

---

### Post by HotForLinux on 2010-05-25
In *[http://manpages.ubuntu.com](http://manpages.ubuntu.com)* I discovered that there are two manpages for *pwd* (and many other commands as well). I have the *manpages-postfix* package installed, but I don't see how can I display the two manpages for pwd.

>> Does somebody know?


Just for the record, this is the other pwd manpage. The one I can't get from the system, taken from the web:
```

**NAME**       pwd - return working directory name

**[B]SYNOPSIS**[/B]

       **pwd** **[-L** **|** **-P** **]**

**[B]DESCRIPTION**[/B]

       The  _pwd_ utility shall write to standard output an absolute pathname of
       the current working directory, which does not contain the filenames dot
       or dot-dot.[B]


OPTIONS[/B]       The  _pwd_  utility  shall  conform  to  the  Base  Definitions volume of
       IEEE Std 1003.1-2001, Section 12.2, Utility Syntax Guidelines.

       The following options shall be supported by the implementation:

       **-L**     If the _PWD_ environment variable contains an absolute pathname of
              the current directory that does not contain the filenames dot or
              dot-dot, _pwd_ shall  write  this  pathname  to  standard  output.
              Otherwise, the **-L** option shall behave as the **-P** option.

       **-P**     The  absolute pathname written shall not contain filenames that,
              in the context of the pathname, refer to files of type  symbolic
              link.

```

---

