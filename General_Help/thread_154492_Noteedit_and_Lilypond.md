---
title: "Noteedit and Lilypond"
date: 2006-04-03
forum: General Help
---

### Post by jazzmuzik on 2006-04-03
It appears that Noteedit 2.7.1 and Lilypond 2.6.3 have an incompatibility, not at the file level though. When Noteedit generates Lilypond output, Lilypond finds incompatibilities when it generates notaton. This seems to be due to Lilypond being ahead of Noteedit. I'm wondering if the newer Noteedit in Dapper (2.8.0) would fix that???  Hope that makes sense.

---

### Post by jazzmuzik on 2006-04-04
I've noticed that a problem developed with Noteedit after installing Ubuntu updates. The ability to edit notation via the keyboard is gone. The keyboard doesn't work at all except for a few things like Ctrl-Z (Undo). I've seen one reference to this on Usenet. Anybody have a solution?

---

### Post by jazzmuzik on 2006-04-04
I just found a solution to the Noteedit keyboard problem. It's detailed below for version 2.8 however it also worked for 2.7.1-2ubuntu . You have to download the source (sudo apt-get source noteedit), fix the permissions to the newly created noteedit source directory (sudo chown -R yourlogin:users ~/noteedit*) install any necessary dependencies and then recompile (debuild). And then reinstall the resulting .deb files of course. I hope that helps somebody. Here's the fix:

[https://developer.berlios.de/bugs/?func=detailbug&bug_id=6263&group_id=2232](https://developer.berlios.de/bugs/?func=detailbug&bug_id=6263&group_id=2232)

Here's a copy of the solution:

I resolved the problem searching on the net :

in the file noteedit/mainframewidget.cpp

replace the line
keys_ = new KAccel(this);
by
keys_ = new KAccel((QWidget*)this->parent());

and that's it !

I describe more in detail, in french, on this page :
[http://cbenz.tuxfamily.org/index.php?n=Main.NoteeditBug](http://cbenz.tuxfamily.org/index.php?n=Main.NoteeditBug)

I provide patched Debian packages :

[http://cbenz.tuxfamily.org/uploads/Main/noteedit_2.8.0-2_i386.deb](http://cbenz.tuxfamily.org/uploads/Main/noteedit_2.8.0-2_i386.deb)
[http://cbenz.tuxfamily.org/uploads/Main/noteedit-data_2.8.0-2_all.deb](http://cbenz.tuxfamily.org/uploads/Main/noteedit-data_2.8.0-2_all.deb)

hope this helps

---

### Post by Gustav on 2006-04-04
This is the biggest drawback with Lilypond (that I have come up with), the syntax changes (a lot) for every new version. (Although there are a script that translates you old lilypond files to the new syntax).

Other than that lilypond is great!!!

---

### Post by jazzmuzik on 2006-04-11
[QUOTE=jazzmuzik]It appears that Noteedit 2.7.1 and Lilypond 2.6.3 have an incompatibility, not at the file level though. When Noteedit generates Lilypond output, Lilypond finds incompatibilities when it generates notaton. This seems to be due to Lilypond being ahead of Noteedit. I'm wondering if the newer Noteedit in Dapper (2.8.0) would fix that???  Hope that makes sense.[/QUOTE]

As mentioned above by Gustav, I found that you have to run convert-ly on your old lilypond (.ly) files in order to update them to the current version. The utility convert-ly reads the version string in your .ly file and outputs a modified .ly that will work with the currrent version of the lilypond. Do something like this on the command line:

convert-ly oldfile.ly > newfile.ly

Note that if you don't have a version string in oldfile.ly it won't work, so you'll have to insert something there. Try and be as accurate as possible. It will look something like this:

\version "2.2.0"

The resulting file (outfile.ly) will contain a new version number similar to this:

\version "2.7.40"

---

