---
title: "Beamer Movie under Okular not Working"
date: 2011-02-12
forum: General Help
---

### Post by rhoparkour on 2011-02-12
Hello,

  I want to embed a movie in a latex beamer presentation. I run Ubuntu 10.04 and I know running pdf embedded movies under Linux is still a problem.

  From what I have been able to dig up, the guys at Okular have partially solved this problem. It seems that Okular under KDE is able to run embedded movies in a pdf presentation. I downloaded it and it doesn't work for my Ubuntu distribution. 

  Can anyone confirm this? Will installing kde through apt-get solve my problem?
```
sudo apt-get install kde
```
I'm asking this because it also seems to be a pain to uninstall KDE and it's components after installing it.

By the way, I am completely open to dual booting into a different distro in order to see my embedded movies, so if anyone has embedded movies working in some other distro, I'm open to installing it!

:popcorn: Have a nice weekend my fellow open source users!

---

### Post by rhoparkour on 2011-02-13
Sorry for the bump, but does anyone have any info?

---

### Post by ptitpoul on 2011-04-10
With Okular 0.11.2 (kde 4.5.3), the example that is posted on [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=593477](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=593477) works when compiled with pdflatex from TeX Live 2009 (kubuntu 10.04). It works with the package *multimedia* but not with *movie15*.

---

### Post by doyleknight on 2011-04-27
This works on my Lenovo X201 running Ubuntu 10.04:

\documentclass[]{beamer}
...
\usepackage{hyperref}
\usepackage{multimedia}
...
\begin{document}
...
\href{run:[nameofmovie].wmv}
     {\includegraphics[options]{[figure-to-appear-before-movie-starts]}}

Compile the LaTeX file and view in Acroread.  Click on the image and the
movie will open in a separate window.  

If your movie is not .wmv, use the convert program

convert [moviename].avi [moviename].wmv

or something similar.

---

### Post by Astro96 on 2012-05-18
I have recently run into the same issue and found that the best solution is to use acroread version 9.4.1 and embed a flash player.  It works well, looks nice, and is stable.  I just used it to give a talk to 100+ researchers.

Here's the full post with all the info: [http://www.abarry.org/likelytobeforgotten/?p=61](http://www.abarry.org/likelytobeforgotten/?p=61)

---

