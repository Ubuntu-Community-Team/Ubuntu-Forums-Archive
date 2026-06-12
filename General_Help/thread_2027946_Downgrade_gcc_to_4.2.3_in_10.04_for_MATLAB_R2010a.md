---
title: "Downgrade gcc to 4.2.3 in 10.04 for MATLAB R2010a"
date: 2012-07-17
forum: General Help
---

### Post by nmatiasz on 2012-07-17
I have MATLAB R2010a installed in Ubuntu 10.04. The default gcc compiler for 10.04 appears to be gcc-4.4; however, MATLAB R2010a requires gcc-4.2.3 for working with MEX. 

I successfully installed gcc-4.1 and set it as my default gcc compiler. I no longer get a compiler warning when I use MEX, but I still can't compile due to other errors. I know that others have used gcc-4.2.3 successfully with the same system specs and build files, so I suspect that I need gcc-4.2.3 to solve my problem.

I'm unable to use "sudo apt-get install" because a gcc-4.2.3 package does not exist for 10.04. All of the tutorials that I've read regarding this issue have covered other versions of both Ubuntu and MATLAB, and I can't figure out how to install gcc-4.2.3 with all of the required libraries, dependencies, etc.

Does anyone have a solution for this particular configuration (Ubuntu 10.04 and MATLAB R2010a)?

---

### Post by spjackson on 2012-07-17
4.2.3 is pretty old. I would not want to replace 10.04's gcc with it.

The options I suggest you consider are these.

[LIST=1]
[*]Install an old o/s e.g. Hardy Heron either in a virtual machine, or as an alternative boot.
[*]Get old package(s). e.g. Hardy Heron (8.04) has 4.2.4. Install them in a chroot.
[*]Build 4.2.3 and associated libraries from source.
[/LIST]
Options 2 and 3 require some expertise in my opinion. I would suggest that the first option is the least error-prone.

---

