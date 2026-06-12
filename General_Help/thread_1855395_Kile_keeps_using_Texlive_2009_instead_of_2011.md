---
title: "Kile keeps using Texlive 2009 instead of 2011"
date: 2011-10-06
forum: General Help
---

### Post by Azrael84 on 2011-10-06
Hi,

So after a clean installation of Ubuntu 11.04, I downloaded the web install-tl to install texlive 2011 doing a full installation following the instructions in the guide [http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#x1-170003.1.1](http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#x1-170003.1.1)

Installation went through fine and I added to my $HOME/.profile 
>   PATH=/usr/local/texlive/2011/bin/i386-linux:$PATH; export PATH 
  MANPATH=/usr/local/texlive/2011/texmf/doc/man:$MANPATH; export MANPATH 
  INFOPATH=/usr/local/texlive/2011/texmf/doc/info:$INFOPATH; export INFOPATH then restarted.

Now when I open the terminal and do 'tex' I see that I am using 2011 instead of the native 2009 shipped with the distro, great. I can compile .tex files and all the rest from the terminal. all seems to be good.

I try and compile something in Kile at this point, but it fails because of being unable to find .sty files (that are definitely in the 2011 texlive package) so I find this is strange and discovered when looking at the output that Kile is actually still using texlive 2009.....sigh....

Now I went back to the terminal as root and did echo $PATH and found that actually as root my PATH variable hadn't changed and when I ran tex at the terminal I got the 2009 verion, so thought maybe this had something to do with it, because perhaps it needed to update the PATH globally or something for Kile to recognise, so I went to etc/environment and added > **PATH="/usr/local/texlive/2011/bin/i386-linux: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" **and went to etc/manpath.config and added > [B]MANPATH_MAP /usr/local/texlive/2011/bin/i386-linux \
              /usr/local/texlive/2011/texmf/doc/man [/B].Now at the terminal running as root tex does show the 2011 version, great (This also means tlmgr runs in root at the terminal which is nice as before it only found tlmgr under user and wouldnt let me make changes to packages). However I try Kile again and nope, still attempting to use 2009.

OK, at this stage I'm totally confused and start googling, I find an article by someone who seems in a very similar situation to me except not ubuntu 11.04,  [http://theunspokenwords.net/blog/Information-Technology/post/kde-environment-variable-configuration-for-configuring-kile-with-texlive-2011](http://theunspokenwords.net/blog/Information-Technology/post/kde-environment-variable-configuration-for-configuring-kile-with-texlive-2011)

The jist is that kile being a KDE application only sees the KDE environment variables so you need to go to the $HOME/kde folder create an env folder and make a file path.sh with the definitions contained in it. I think this is finally going to solve it for me, restart, hurriedly run Kile, but nope same errors again!

---

### Post by Azrael84 on 2011-10-06
I next found the thread at [http://ubuntuforums.org/showthread.php?t=1311444&highlight=texlive+2009](http://ubuntuforums.org/showthread.php?t=1311444&highlight=texlive+2009) and this prompted mean to remove the PATH= lines I had previously added to my .profile and replace with (changing 2011 to 2009 and x86_64 with i386 etc):

> 
# set PATH so it includes user's private bin if it exists if [ -d "$HOME/bin" ] ; then     PATH="$HOME/bin:$PATH" fi if [ -d "/usr/local/texlive/2009/bin/x86_64-linux" ] ; then     PATH="/usr/local/texlive/2009/bin/x86_64-linux:$PATH" fi if [ -d "/usr/local/texlive/2009/texmf" ] ; then     export TEXMFMAIN="/usr/local/texlive/2009/texmf" fi if [ -d "/usr/local/texlive/2009/texmf-dist" ] ; then     export TEXMFDIST="/usr/local/texlive/2009/texmf-dist" fi if [ -d "/usr/local/texlive/texmf-local" ] ; then     export TEXMFLOCAL="/usr/local/texlive/texmf-local" fi if [ -d "$HOME/texmf" ] ; then     export TEXMFHOME="$HOME/texmf" fi if [ -d "$HOME/.texlive2009/texmf-config" ] ; then     export TEXMFCONFIG="$HOME" fi if [ -d "/usr/local/texlive/2009/texmf-config" ] ; then     export TEXMFSYSCONFIG="/usr/local/texlive/2009/texmf-config" fi if [ -d "$HOME/.texlive2009/texmf-var" ] ; then     export TEXMFVAR="$HOME" fi if [ -d "/usr/local/texlive/2009/texmf-var" ] ; then     export TEXMFSYSVAR="/usr/local/texlive/2009/texmf-var" fi
Another restart, and another attempt at Kile, still no joy, but now a slightly 
different error:

>   This is TeX, Version 3.1415926 (TeX Live 2009/Debian)
 ---! /usr/local/texlive/2011/texmf-var/web2c/tex/tex.fmt doesn't match tex.pool
 (Fatal format file error; I'm stymied)which at least seems to suggest even though it is still using 2009, it's searching for something in the right place

Anyone have an idea how I can resolve this and get Kile using 2011?

---

### Post by Azrael84 on 2011-10-06
Just to add one more attempt: I also just tried the procedure outlined here [http://tex.stackexchange.com/questions/23869/how-to-configure-kile-to-run-texlive-2011](http://tex.stackexchange.com/questions/23869/how-to-configure-kile-to-run-texlive-2011)

>  
export PATH=/usr/local/texlive/2011/bin/`uname -i`-linux:$PATH export MANPATH=/usr/local/texlive/2011/texmf/doc/man:$MANPATH export INFOPATH=/usr/local/texlive/2011/texmf/doc/info:$INFOPATH unset TEXINPUTS unset TEXMFCONFIG



in etc/profile.d/zzzz.texlive.sh

but although my terminal command latex-v testifies to me using 2011, kile 
still just isn't having it.

What's going wrong??

---

### Post by Azrael84 on 2011-10-07
Sorry about the long posts, but does anyone have any idea? TexMaker is working fine and it is using the 2011 version, seems it's just Kile having issues...

---

