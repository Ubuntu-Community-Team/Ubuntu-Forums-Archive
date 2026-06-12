---
title: "Matlab 2009a Custom Launch"
date: 2009-09-04
forum: General Help
---

### Post by Red.Dragon on 2009-09-04
I installed Matlab 2009a Student Version on my Ubuntu 9.04 machine.

To install Matlab and run it I had to using the -glnx86 tag, as are no 64-bit instructions with the program. 

The program works fine, but only when I launch ```
/usr/local/matlab2009a/bin/matlab -glnx86
``` from the terminal. I don't need the directory in order to make the program work, but that's just to show where I have the program installed.

I'm guessing the problem is with Java because when I launch from AWN the splash screen comes up and disappears and the -desktop tag does nothing.

I tried a little addition to get it to run, but I get an error. 

```

matthew@Trius:/usr/local$ export AWT_TOOLKIT=MToolkit ; matlab -glnx86
Unable to initialize com.mathworks.mwswing.MJStartup
Fatal Error on startup: Failure loading desktop class

```So I confirmed it's a problem with Java, but I haven't the slightest idea on what to do. 

I tried to fix MATLAB_JAVA: 

```

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.16/jre/

```And I can't launch the program from AWN, but I can launch it from the terminal, the problem though is that it no longer launches, but that the program then is in the terminal. 

I have everything back to the way it was when I first installed. 

Any suggestions?

---

### Post by XCan on 2009-09-04
I dunno why it would not work for you, I have a launcher on my desktop, but I presume that the same should work for you using AWN. The launcher uses ```
 /usr/local/matlab/bin/matlab -desktop 
``` as command. However, I think your export thingie should better be ```
 export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.16/jre/ 
``` I would add that line to Matlab's launcher script though, just slam it in at the top of /usr/local/matlab2009a/bin/matlab

---

### Post by Red.Dragon on 2009-09-04
Oh I made a typo. I did have the = in there. It did me no good though.
That's what causes the program to launch IN the terminal, so no GUI.

And the -desktop tag does not work with the -glnx86 tag. 

I have to use the glnx86 tag in order to make the program run on my 64-bit machine. 

I'm pretty sure it's just a problem with Java that I don't know how to fix.

---

### Post by Nepherte on 2009-09-04
I've never had to use the -glnx86 switch so I doubt there were no 64 bit instructions included in matlab.

---

### Post by Red.Dragon on 2009-09-04
I checked. There were none with the Student Version that I have.

I checked and I don't have the ability to download any 64-bit Matlab from their website. 

But the -glnx86 tag was the only way I was able to install as well.

---

### Post by Red.Dragon on 2009-09-08
Any ideas on how I might fix Java for MatLAB?

---

