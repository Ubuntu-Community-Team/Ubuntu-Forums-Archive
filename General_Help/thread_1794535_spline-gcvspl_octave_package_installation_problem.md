---
title: "spline-gcvspl octave package installation problem"
date: 2011-07-01
forum: General Help
---

### Post by Jo30230 on 2011-07-01
Hello everyone
I am almost new in Ubuntu and Octave. I installed Octave3.4.2 on my Ubuntu 10.4. I managed to install properly some new package I needed (symbolic, spline, algebra...). But I now have problem to install the spline-gcvspl package. 
When I do the thing (pkg install spline-gcvspl-1.0.8.tar.gz), I do'nt get any error message. But after, Octave does'nt recognize csaps function (included in this package).
Moreover, it seems that the package is well installed since when I ask the installed package list (pkg list) I get :
 p, li { white-space: pre-wrap; }  [COLOR=#000000][FONT=Liberation Mono]Package Name       | Version | Installation directory[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]-------------------+---------+-----------------------[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]          general *|   1.2.2 | /usr/share/octave/packages/general-1.2.2[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]          gnuplot  |   1.0.1 | /usr/share/octave/packages/gnuplot-1.0.1[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]            image *|  1.0.14 | /usr/share/octave/packages/image-1.0.14[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]      integration  |   1.0.7 | /usr/share/octave/packages/integration-1.0.7[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]   linear-algebra *|   2.0.0 | /usr/share/octave/packages/linear-algebra-2.0.0[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]    miscellaneous *|  1.0.11 | /usr/share/octave/packages/miscellaneous-1.0.11[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]missing-functions *|   1.0.2 | .../share/octave/packages/missing-functions-1.0.[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]2[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]           odepkg *|  0.6.12 | /usr/share/octave/packages/odepkg-0.6.12[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]            optim *|  1.0.16 | /usr/share/octave/packages/optim-1.0.16[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]      optiminterp *|   0.3.3 | /usr/share/octave/packages/optiminterp-0.3.3[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]             plot *|   1.0.8 | /usr/share/octave/packages/plot-1.0.8[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]       quaternion *|   1.0.0 | /home/jonathan/octave/quaternion-1.0.0[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]           signal *|  1.0.11 | /usr/share/octave/packages/signal-1.0.11[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]          specfun *|   1.0.9 | /usr/share/octave/packages/specfun-1.0.9[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]   special-matrix *|   1.0.7 | /usr/share/octave/packages/special-matrix-1.0.7[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]    spline-gcvspl  |   1.0.8 | /home/jonathan/octave/spline-gcvspl-1.0.8[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]          splines *|   1.0.7 | /usr/share/octave/packages/splines-1.0.7[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]       statistics *|  1.0.10 | /usr/share/octave/packages/statistics-1.0.10[/FONT][/COLOR]
 [COLOR=#000000][FONT=Liberation Mono]           struct *|   1.0.9 | /usr/share/octave/packages/struct-1.0.9[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Mono]Does anybody understand why csaps function still doesn't work?[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Mono]Thank you
[/FONT][/COLOR]

---

