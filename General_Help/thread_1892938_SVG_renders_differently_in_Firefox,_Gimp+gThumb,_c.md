---
title: "SVG renders differently in Firefox, Gimp+gThumb, convert, OpenOffice, and Inkscape"
date: 2011-12-09
forum: General Help
---

### Post by kerryhall on 2011-12-09
I have an svg that I made in gedit/scripting, but it renders differently in five different programs. This is not good.

Gimp+gThumb give the same results, only two that match so far, but the text is not where I want it.

Inkscape and Firefox seem to get the text placement right, but Inkscape renders paths wrong.

Openoffice renders text, lines, and paths wrong. Only circles are right.

Convert (command line tool) to png seems to get font wrong, text size wrong, and line rendering wrong.

Firefox has everything looking like how I want it, but of course it can't convert to a png.

Even **if** I am screwing up the syntax somehow (and I doubt it, as all I am doing are commands like <circle cx="3.5671875" cy="1.06664053826" r="0.008" style="fill:white"/> ), shouldn't it render the same in each program? Or at least give an error?

Which of these is the *correct* rendering? If I send a company this svg to get made into a poster, which one is it going to look like to them?

firefox:
Version 8.0

convert:
Version: ImageMagick 6.5.7-8 2010-12-02 

Inkscape:
version 0.48

OpenOffice:
version 3.2

Gimp:
Version 2.6

Thanks!!

---

### Post by sanderd17 on 2011-12-09
I know in Inkscape, you can store an image as plain SVG, or as inkscape SVG. So there are differences between SVG implementations.

Maybe you can take a look at Batik, that seems to have a very complete SVG implementation.

[https://en.wikipedia.org/wiki/Batik_%28software%29](https://en.wikipedia.org/wiki/Batik_%28software%29)

---

### Post by kerryhall on 2011-12-09
There might be extensions to svg, which is what I am assuming inkscape has, but a static file should look the same in different svg renderers, should it not? 

Thanks! I'll give Batik a try. If it renders the same as GIMP and gThumb, I'll go with that text orientation as correct. If there are other issues, I will report back here.

Although I would like to see this resolved so that each piece of software renders svgs correctly, but not sure how to start working on that haha.

---

### Post by kerryhall on 2011-12-29
Batik renders the same as firefox....hahaha now what? Shouldn't they all render the same?

---

### Post by sanderd17 on 2011-12-30
Since batik is considered as one of the most complete implementations, I would go with that one, but maybe you can export it to PDF or EPS if you send it to someone.

EPS and PDF seem to be standards that are more simple to implement (but not to edit), and thus there are less problems with different renderings.

I've worked a lot with EPS and PDF, in different readers, created by a bunch of programs, and they never seem to change.

---

