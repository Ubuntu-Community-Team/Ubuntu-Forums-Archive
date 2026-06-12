---
title: "Nano &amp; line breaks"
date: 2009-12-11
forum: General Help
---

### Post by sisyphus1978 on 2009-12-11
So I've been trying hard to dedicate my text-editing life to nano (I don't want/need vi/vim/emacs), but I just can't get my head around the line breaks, line wraps or whatever you want to call it. All I want is a notepad type functionality ie write plain text and get out plain text, no unnesary linebreaks or formatting. Every time I think I have it figured, I don't. D'oh. I've got a nanorc file and I've checked the man pages etc and I'm stumped.

E.g:

I paste a long line of lorem ipsom into nano. I alt-l. The text wraps. I open that file in gedit and then paste into firefox, and it's got a load of iinebreaks (I dunno how to paste out from nano - although the same happens writing in w3m - with nano as editor).

Here is my nanorc (though I've tried lots of settings):
> set speller "aspell -c"
set morespace
set nohelp
unset nowrap
set fill -2
set tempfileAny ideas?

---

### Post by Bachstelze on 2009-12-11
Just a guess, I don't use nanorc, but I believe you want to replace [font=monospace]unset nowrap[/font] with [font=monospace]set nowrap[/font]. Alternatively, call nano with the [font=monospace]-w[/font] switch.

---

### Post by sisyphus1978 on 2009-12-11
I had tried quite a few obvious things, and that was one of them. Set nowrap leads to one long line (with a $ denoting further content up the line). What I want is nano to wrap according to the size of the screen, but to not insert any page breaks in the absence of a hard carriage return.

Like in notepad (windoze) where you select linewrap, but it doesn't add formatting. Am I explaining it clearly. Are we all (if you pardon the pun) on the same page...

:)

---

### Post by sisyphus1978 on 2009-12-12
I've found a couple of discussions about this. I don't quite understand the technicalities but I think it may be a bug?

>  [Please sync nano 2.0.9-2 from Debian unstable [was: Breaks config files by adding hard line breaks]]("https://bugs.launchpad.net/debian/+source/nano/+bug/39866") And I found this discussion over on an [arch forum]("http://bbs.archlinux.org/viewtopic.php?id=52824").

nano -V outputs > GNU nano version 2.0.9 (compiled 10:27:02, Mar 30 2009)
 (C) 1999, 2000, 2001, 2002, 2003, 2004, 2005, 2006, 2007
 Free Software Foundation, Inc.
 E-mail: [EMAIL="nano@nano-editor.org"]nano@nano-editor.org[/EMAIL]    Web: [http://www.nano-editor.org/](http://www.nano-editor.org/)
 Compiled options: --disable-wrapping-as-root --enable-color --enable-extra --enable-multibuffer --enable-nanorc --enable-utf8
Do I have to upgrade to 2.0.9-2 to get around this feature?

Currently perplexed. :)

---

### Post by efflandt on 2009-12-12
nano is a terminal editor so it really does not know anything about gui copy and paste things.  Either it word wraps, or with -w it does not.

Simply use a wider terminal (like 132x24) which you can do on the fly, or I also widen gedit window when using that.

---

### Post by sisyphus1978 on 2009-12-17
I don't know how I missed this but the man page reveals this:
> Enable 'soft wrapping'.  nano will attempt to display the entire contents of a line, even if it is longer than the screen width.  Since '$' normally refers to a variable in the Unix shell, you should specify this option last when using other options (e.g. 'nano -wS$') or pass it separately (e.g. 'nano -wS -$').       However I couldn't get nano to work using that command. And I found this on a nano mailing list:

> *  Unfortunately, there is currently no "soft-wrap"*
>* option in nano.  All wrapping nano does is hard wrapping.  There is a*
>* way to work around it, though.  After you've finished editing a file,*
>* hard wrapping and all, you can reopen it with the -r option set to a*
>* very high value (say 10000) and justify the lines you want to be long.*
>* Of course, this assumes that no long line in the file will be longer*
>* than 10000 characters, but you can always increase the value if you need*
>* to.*Now I don't think I'm asking for anything too difficult. I want to use nano as my main text input/edit program. I also want to use it as the default in w3m. But with the linebreaks all over the place (leading to broken up sentences) it just becomes too much hard work.

Other than suggesting gedit or any other packages, has anybody got any other solutions? I am going to try and upgrade my nano package and see if tha helps.

---

### Post by sisyphus1978 on 2009-12-17
For anyone interested I believe I have it. I upgraded to [nano 2.2.0-1]("http://packages.debian.org/sid/nano"), commented out nowrap in /etc/nanorc and then created a new file with ```
nano -w -$ filename 
```Nano then wraps within the file and according to the window size. Something I like because of the different sizes of the displays I use (a small eeepc 8 inch screen and a large 40 inch tv). I will get back to testing it, but assume this is the solution.

---

### Post by sisyphus1978 on 2009-12-17
Here is a copy of my nanorc (for completedness sake):

```
set speller "aspell -c"
set morespace
set nohelp
set tempfile
set nowrap
set wordbounds
set softwrap
```Note: Even though w3m uses nano, I can't seem to stop it adding in hard breaks. But nano regular seems good.

---

### Post by VCoolio on 2009-12-17
Thanks for figuring this out. The debian link didn't load, but I compiled the source for the lucid nano package on my karmic and it works fine. Made an alias nano='nano -w$' because ^l enabled line wrapping but didn't actually do it; is there an other keybinding for that?

---

### Post by sisyphus1978 on 2009-12-17
The deb is working again. :) I don't really get what you're asking. Check here:

[http://savannah.gnu.org/projects/nano/](http://savannah.gnu.org/projects/nano/)
[http://www.nano-editor.org/docs.php](http://www.nano-editor.org/docs.php)

---

### Post by llamabr on 2010-04-07
Can I use apt to upgrade my nano?  I dloaded the deb, force installed the 2.2-11 deb, but it complains about needing an updated glibc.  I don't want to start messing with that.

Is there a simple way to tell apt to get a newer version, along with all of the dependencies?

---

### Post by sisyphus1978 on 2010-04-08
I didn't do anything special except install the deb. I've moved on to gedit and latex now. Good luck with it though.

---

