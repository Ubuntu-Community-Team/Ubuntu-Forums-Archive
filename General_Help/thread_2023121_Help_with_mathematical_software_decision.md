---
title: "Help with mathematical software decision"
date: 2012-07-12
forum: General Help
---

### Post by thedoctor81877 on 2012-07-12
Hullo all.

I am starting a new job authoring solutions for math textbooks, and I am fairly proficient in LateX, but not so in programs used for drawing graphs. For most of what I will be doing I shall need to graph areas under curves (visualization for iterated integrals) such as:
1. Graph and shade the portion of a circle with radius 4, and from 0 \leq \theta \leq 3\pi/2
2. Graph and shade the inside of a triangular region with vertices (-1,0), (0,0), and (1,0)

I am somewhat pressed on time, and so here's my ultimate question: What s the best software for doing what I need  - TikZ, Inkscape, Libre Office Calc or Draw, R, Sage, or some other software- Currently I am having a big dilemma deciding which is best and hence I have not learned much of anything regarding these softwares. I really want the one that is fairly easy to use, and looks professional Thanks a bunch,and let me know if I need to put down more info. 
-Michael D

---

### Post by Redblade20XX on 2012-07-12
Most math books I've read have used MatLab for representation of diagrams such as the integrations in integral calculus and vector calculus. You'll have to spend time learning the commands in any software so it might not be quick, depending on you of course. 

 MatLab is proprietary software that requires you to know about some programming but you can use GNU Octave as a "decent" freed substitution (still requires programming though). 

[http://www.gnu.org/software/octave/](http://www.gnu.org/software/octave/)

- Red

---

### Post by nmaster on 2012-07-12
I think that Sage would work well and its free.  Since Sage uses Python, you could directly use Python with matplotlib .  The only problem with using Sage/Python (or Matlab for that matter) is that there is less structure and it isn't WYSIWYG. Once you get going, it should be great though.  For instance, it should be too hard to write a function that takes a list of points and draws a polygon.

There are other options as well:
-- Xfig [http://seb-motsch.com/create-beautiful-figures-for-latex-with-xfig/](http://seb-motsch.com/create-beautiful-figures-for-latex-with-xfig/)
-- ePiX [http://mathcs.holycross.edu/~ahwang/epix/images/gallery-1.2/index.html](http://mathcs.holycross.edu/~ahwang/epix/images/gallery-1.2/index.html)

I would personally go with Python+matplotlib.  There will be a learning curve, but if you're writing solutions for a textbook you'll end up being able to reuse code.  Once you get the hang of it you'll have some pretty slick figures that should be easy to tweak. 

As an undergrad/grad student I always used LaTeX to do math/engineering homeworks and I liked using Python to do the figures whenever possible.

---

