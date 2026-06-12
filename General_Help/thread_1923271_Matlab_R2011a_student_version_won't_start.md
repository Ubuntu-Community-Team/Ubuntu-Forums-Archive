---
title: "Matlab R2011a student version won't start"
date: 2012-02-10
forum: General Help
---

### Post by jumplajz on 2012-02-10
Hi,
I'm having troubles starting Matlab after I updated the system to Ubuntu 11.10. At first I was getting the error described here [http://www.mathworks.com/support/solutions/en/data/1-F68FSA/index.html?solution=1-F68FSA](http://www.mathworks.com/support/solutions/en/data/1-F68FSA/index.html?solution=1-F68FSA) so I solved the problem according to the recipe but now if I go to the folder where Matlab is installed and run ./matlab I get the error "Could not write to the file ....../activation.xml because of file permissions problem". So I run it as sudo, I get no error but Matlab doesn't start.
Any help would be appreciated!

---

### Post by hwttdz on 2012-02-10
Can you change permissions of the ....../activation.xml file, i.e. "chmod a+w ....../activation.xml" and try again as your user.  Also [s]in general[/s] sudo is not the answer to this sort of issue.

---

