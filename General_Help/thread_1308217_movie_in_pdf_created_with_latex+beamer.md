---
title: "movie in pdf created with latex+beamer"
date: 2009-10-31
forum: General Help
---

### Post by g.a. on 2009-10-31
Hi,

after having read tons of posts I still not have found my solution.

The problem is embed/run a video under a pdf file made with latex+beamer.

I need to use latex+dvips+ps2pdf and not pdflatex for compatibility with other packages.

Several questions about:

1) package movie15 + \includemovie command. Acroread+realplayer does not work. I had several troubles, read somewhere that in Linux it does not work. If someone has any idea is welcome. 

2) package multimedia + \includemovie command (default for the beamer manual). It does not work under evince, okular or Acrobat. In the first two it simply does nothing when clicking on the image, under Acrobat it says "cannot find player..." (the latter is normal)

3) package hyperref + command \href{run:Video.avi}. Ok under all the pdf viewer. The only problem is that it opens mplayer on a new window.

4) package hyperef + \href{run:myscript.mysh}. Where myscript.mysh is an executable file with a single line command that run mplayer without borders so that it seems embedded in the presentation. The problem is the same with all the pdf viewer, it open a text editor to edit the script. I know that I should change something related to the default actions in nautilus but all the posts say it as if it was trivial and for me is not...

5) what about portability? often, in the very last minute, during the conferences/meeting we decide to copy all the ppt/pdf on one single machine and it is always a Windows one...

Finally, what is a little bit frustating is that, before moving to ubuntu, I had a kubuntu 9.04 installation where the solution 2 worked very well with okular.

Tanks,
g.


Some useful posts already read:

[http://www.uoregon.edu/~noeckel/PDFmovie.html](http://www.uoregon.edu/~noeckel/PDFmovie.html)

[http://greekbitches.blogspot.com/2008/07/embedded-movies-in-latex-pdf-workaround.html](http://greekbitches.blogspot.com/2008/07/embedded-movies-in-latex-pdf-workaround.html)

[http://ubuntuforums.org/showthread.php?t=592859](http://ubuntuforums.org/showthread.php?t=592859)

---

### Post by ludovicovan on 2009-11-05
> **g.a. said:**
> Hi,

 Finally, what is a little bit frustating is that, before moving to ubuntu, I had a kubuntu 9.04 installation where the solution 2 worked very well with okular.



okular (as every kde app) uses the phonon library for multimedia. I think you should install the phonon package.

For the other questions i think you'll have better luck asking in a latex specific forum.

bye

---

### Post by g.a. on 2009-11-06
Thanks, phonon seems to be already installed:

```
sudo aptitude search phonon
p   libphonon-dev                                             - development files for the Phonon multimedia framework               
i A libphonon4                                                - Phonon multimedia framework for Qt 4                                
i A phonon                                                    - metapackage for Phonon multimedia framework                         
v   phonon-backend                                            -                                                                     
p   phonon-backend-gstreamer                                  - Phonon GStreamer 0.10.x backend                                     
p   phonon-backend-null                                       - Phonon null backend (no real backend)                               
i A phonon-backend-xine                                       - Phonon Xine 1.1.x backend                                           
p   phonon-dbg                                                - Phonon debugging symbols                                            
p   python-qt4-phonon                                         - Python bindings for Phonon                                          
p   python-qt4-phonon-dbg                                     - Python bindings for Phonon (debug extensions)                       
v   python2.5-qt4-phonon                                      -                                                                     
v   python2.5-qt4-phonon-dbg                                  -                                                                     
v   python2.6-qt4-phonon                                      -                                                                     
v   python2.6-qt4-phonon-dbg                                  -                                                                 
```

yes, I have posted a little bit every where this post, it seems that this problem is not diffused...

thanks again. best,
g.

---

### Post by rosencrantz on 2010-04-20
Just a quick update regarding one of g.a.'s links: We moved the G(r)eek Bitches' Blog to an address less threatened by bowdlerisation, the mplayer workaround howto can now be found here:
[http://eumenidae.blogspot.com/2008/07/embedded-movies-in-latex-pdf-workaround.html]("http://eumenidae.blogspot.com/2008/07/embedded-movies-in-latex-pdf-workaround.html")

Sorry for the inconvenience - honi soit qui mal y pense.

rosencrantz

---

### Post by Astro96 on 2012-05-18
Finally found a solution for this -- too me a long time!  I'm using acroread 9.4.1 with an embedded flash player.

Here's the full info: [http://www.abarry.org/likelytobeforgotten/?p=61](http://www.abarry.org/likelytobeforgotten/?p=61)



- Andy

---

### Post by g.a. on 2012-05-20
Thanks for posting, I tried your example with acroread 9.5.1 under ubuntu 11.10 and unfortunately it does not work.

it gives a "3d data parsing error".

best
g.

---

### Post by Astro96 on 2012-05-20
Yes, you need version 9.4.1.  You'll see that you can install it without using apt (and thus not dealing with version issues there) at the link.



Andy

---

