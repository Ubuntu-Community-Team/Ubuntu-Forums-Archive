---
title: "Octave plotting issue"
date: 2011-03-26
forum: General Help
---

### Post by xshagy on 2011-03-26
I am using octave to create a plot with two curves on it with a legend labeling each curve.  The following code plots each curve and adds a label to the legend.

```
plot(time_Ey,Ey_analytic,'b');	# add analytical vector to plot
legend("Analytical Output");	# add label to legend
hold on;			# hold on	
plot(time_Ey,Ey(:,loc_D+1),'r');# add simulated vector to plot
legend("Simulation Output");	# add label to legend
hold off;			# hold off
```

My problem is, this code works perfectly on my netbook but not on my desktop.  The legend should have two entries; "Analytical Output" with a blue line next to it, and "Simulated Output" with a red line next to it.  When I run it on my desktop, the legend only has only entry in it: "Simulated Output" with a blue line next to it.  It seems like it is only processing the second legend command and linking it to the first plot command.

Netbook Info: Ubuntu 10.04 Netbook
		Octave: version 3.2.3
		gnuplot: Version 4.2 patchlevel 6
Desktop Info: Ubuntu 10.10 Desktop
		Octave: version 3.2.4
		gnuplot: version 4.4 patchlevel 0

I have tried many different methods to get my desktop to produce a proper legend but I am out of ideas.  
I tried adding clf in the beginning, to clear the plot.  
I tried moving the hold command around.  
I tried using one legend command with the following code.  It produced a legend with both entries, but put a blue line next to both.

```
legend("Analytical Output","Simulated Output");
```

I am stumped, any help or suggestions would be greatly appreciated.  Thanks in advance.

---

### Post by xshagy on 2011-04-07
I found some bug reports from others talking about a similar plotting issue.  

There is a new stable release of octave (octave3.4.0) but it doesn't seem to be available from the software center yet.  I downloaded the tarball from gnu.org and attempted to install it from source but I am confused about a dependency issue.

I get the following warnings when I run the configure file.

```
configure: WARNING: OpenGL libs (GL and GLU) not found. Native graphics will be disabled.
configure: WARNING: 
configure: WARNING: I didn't find the necessary libraries to compile native
configure: WARNING: graphics.  It isn't necessary to have native graphics,
configure: WARNING: but you will need to have gnuplot installed or you won't
configure: WARNING: be able to use any of Octave's plotting commands
```

Although, when I search for "OpenGL" in the software center, it says it is installed.

My question is, what exactly is native graphics and if OpenGL is already installed, what am I missing?

Thanks for the help.

---

### Post by xshagy on 2011-10-03
Recent versions of Octave do not seem to support legend creation using the method in my original post.  I figured I would share an alternative method and set this post as solved.

Store all legend annotations in a cell array and call the legend function once with the cell array as the only argument.....

```

x = linspace(1,20,10);	    # x-axis data
y1 = linspace(5,10,10);	    # curve 1 data
y2 = linspace(5,30,10);	    # curve 2 data
legend_list = {"y1","y2"};  # cell array

plot(x,y1,'b');		# add curve one to plot
hold on;		# hold on	
plot(x,y2,'r');		# add curve two to plot
legend(legend_list);	# add legend entries for curve 1 and 2
hold off;		# hold off

```

---

### Post by mahanew on 2013-05-02
hi, 
i'm trying to plot graphs with octave under ubuntu 12.04lts .It is possible to tape:
octave input-file-name ?

Thank you for your help.

---

### Post by xshagy on 2013-05-02
To tape?  I'm not sure I understand what you're asking.  Could you be more descriptive?

You can run octave scripts from the shell.  Is that what you're asking?  Take a look at the manual to see the options....man octave.

---

