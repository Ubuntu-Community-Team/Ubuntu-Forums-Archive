---
title: "Sniglet: tail +n &lt;file&gt; mistakes the +n for a file name"
date: 2009-11-19
forum: General Help
---

### Post by rpaskudniak on 2009-11-19
Here's a nit-picky issue:

I have been using the [FONT="Courier New"]tail +n *file*[/FONT] command for years. For example, if I want to print a file but skip the first 4 lines, I would use > tail +5 to start the output with line 5.

Consider this little session:
> rasputin@chief:~/scratch$ tail +2 all-postinst 
tail: cannot open `+2' for reading: No such file or directory
==> all-postinst <==
/var/lib/dpkg/info/libbsd0.postinst
/var/lib/dpkg/info/libmetacity0.postinst
/var/lib/dpkg/info/ibus.postinst
/var/lib/dpkg/info/psh.postinst
/var/lib/dpkg/info/libmenu-cache0.postinst
/var/lib/dpkg/info/gnome-blackjack.postinst
/var/lib/dpkg/info/libslp1.postinst
/var/lib/dpkg/info/nautilus-data.postinst
/usr/share/doc/libxml-sax-perl/examples/libxml-foo-perl.postinst
/usr/share/doc/xml-core/examples/foo.postinst
Hey! It didn't recognize the +2 as a command option; rather it treated it like a file.  And indeed, for the file itself, it displayed the last 10 lines.

Note: In the man page on tail, it does list the +N option:
> -n, --lines=N
 output the last N lines, instead of the last 10; or use +N to output lines starting with the Nth


I was unable to report this as a bug in the launchpad because "tail" is not a package.  Unless I am somehow invoking it incorrectly, I claim this is a bug.

Just for jollies, I installed the inotail package.  To my display, it behaves the same way.  I removed it.

Anyone wanna replicate my experiment and prove the bug?

---

### Post by dcstar on 2009-11-19
> **rpaskudniak said:**
> Here's a nit-picky issue:

I have been using the [FONT="Courier New"]tail +n *file*[/FONT] command for years. For example, if I want to print a file but skip the first 4 lines, I would use  to start the output with line 5.

Consider this little session:

Hey! It didn't recognize the +2 as a command option; rather it treated it like a file.  And indeed, for the file itself, it displayed the last 10 lines.

Note: In the man page on tail, it does list the +N option:


I was unable to report this as a bug in the launchpad because "tail" is not a package.  Unless I am somehow invoking it incorrectly, I claim this is a bug.

Just for jollies, I installed the inotail package.  To my display, it behaves the same way.  I removed it.

Anyone wanna replicate my experiment and prove the bug?
This outputs the last 5 lines:
```
tail -n5 filename
```
This outputs the whole file starting at that line number, just as the man page says it will:
```
tail -n+5 filename
```
There is no "bug". There may have been different behaviour previously, but it has probably been changed to the appropriate standard now.

---

### Post by rpaskudniak on 2009-11-20
dcstar,
Thank you for pointing out this omission.  I am booted Windows right now so I can't confirm everything.  I do recall, however, that the man page on tail mentioned only using +N for starting at line N; I don't recall seeing +nN (or -nN for that matter) in said Man page.

However, since I also recall that [FONT="Courier New"]*tail -5 file*[/FONT] worked, it would have behooved the command to be written for +5 to work just as well.

As for calling it a bug or not:  I might concede the point but it is usually bad practice to change the accustomed behavior of any utility.  To do so has a tendency to break scripts that are already in action.  I have several scripts published in the IIUG.org Software Library that deliberately skip heading lines of the Informix utilities' output.  Since I have plans to install Informix on my Ubuntu box, it is a matter of concern to me.

(Without revealing my true name here, any Informix aficionados on this forum will probably recognize me from my sign-off and writing style.)

That said,  it may be worth finding out if the -nN option works in other versions of Linux/Unix and adjust my scripts accordingly.

---

### Post by phillw on 2009-11-20
> **rpaskudniak said:**
> dcstar,
Thank you for pointing out this omission.  I am booted Windows right now so I can't confirm everything.  I do recall, however, that the man page on tail mentioned only using +N for starting at line N; I don't recall seeing +nN (or -nN for that matter) in said Man page.

However, since I also recall that [FONT=Courier New]*tail -5 file*[/FONT] worked, it would have behooved the command to be written for +5 to work just as well.

As for calling it a bug or not:  I might concede the point but it is usually bad practice to change the accustomed behavior of any utility.  To do so has a tendency to break scripts that are already in action.  I have several scripts published in the IIUG.org Software Library that deliberately skip heading lines of the Informix utilities' output.  Since I have plans to install Informix on my Ubuntu box, it is a matter of concern to me.

(Without revealing my true name here, any Informix aficionados on this forum will probably recognize me from my sign-off and writing style.)

That said,  it may be worth finding out if the -nN option works in other versions of Linux/Unix and adjust my scripts accordingly.

I've always used -n for tail in both AT&T propriotary UNIX and other linuxes - wasn't aware some used +n !! ... You learn something new everyday !!

Phill.

---

### Post by rpaskudniak on 2009-11-29
Phill,
Always glad to contribute knowledge, rather than always parasiting (is that a real verb? :)  ) on the knowledge of others.

That said, I am now booted Ubuntu so I can check out some options.

[LIST]
[*]tail -30 <file> works exactly as expected - the last 30 lines of the file.
[*]tail -n30 behaves exactly like tail -30.  Hitherto unknown option for me.
[*]tail +30 yields error:
   tail: cannot open `+30' for reading: No such file or directory.
This is what triggered my complaint in the first place.
[*]tail +n30 gives me:
   tail: cannot open `+n30' for reading: No such file or directory
[*]tail -n+30 gives me the file, starting at line 30, what I originally wanted from tail +30 when I started this thread.
[/LIST]

The man page for tail mentions the +N option but in context it is confusing:
>        -n, --lines=N
              output  the  last  N lines, instead of the last 10; or use +N to output lines starting with the Nth

After I install Informix on my box, I will see if my scripts have been broken by this "feature"; I can add some intelligence to the code if indeed I run into problems.

Thanks for the advice and making me look more closely at the man page.

---

