---
title: "matlab's issue with Compiz/Beryl"
date: 2010-10-08
forum: General Help
---

### Post by silencej on 2010-10-08
Why does MATLAB start with a blank grey window when using a Compiz or Beryl window manager? Especially when ssh -Y to a matlab server.

The link by Matlab gives a solution:
[http://www.mathworks.com/support/solutions/en/data/1-30BSFV/?solution=1-30BSFV](http://www.mathworks.com/support/solutions/en/data/1-30BSFV/?solution=1-30BSFV)

I want to keep the visual effect. But the method

> 
To enable the MATLAB desktop with desktop effects enabled, you can set the following environment variable:

AWT_TOOLKIT=MToolkit


can't work for me.

The link's another solution is to upgrade the jre to 1.6. Does it work? If it does, i will write to the IT group.

---

### Post by silencej on 2010-10-09
It's now confirmed that old version jre is conflicted with Compiz/Beryl. So the easist way is to turn off the visual effect.

But i dont' want to. After several trials and failours, i finally succeeded. Here is my solution:

Download the newest jre (for some Matlab server, it's linux 64-bit. Use  "uname -a"). Install the jre.bin in ~/bin dir. The installation doesn't  require the root right, which is exciting and important. For now, the  latest version is 1.6.0_21.
You will find the rt.jar in jre1.6.0_21/lib. So,
```
export MATLAB_JAVA=~/bin/jre1.6.0_21
```
exit ssh, and ssh -Y again. Matlab now lives happily with Compiz.

Reference:
[http://cogmod.osu.edu/wiki/index.php/Matlab_Beryl_Conflict](http://cogmod.osu.edu/wiki/index.php/Matlab_Beryl_Conflict)

---

