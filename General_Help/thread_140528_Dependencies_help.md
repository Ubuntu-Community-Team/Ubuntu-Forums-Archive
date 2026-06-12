---
title: "Dependencies help"
date: 2006-03-06
forum: General Help
---

### Post by interse on 2006-03-06
I need three dependencies to install a program:  Python  v 2.3+,  GTK+  2.6+ and PyGTK 2.6+.

I suspect that these may already be on my Breezy file system.  I did a search for each of these.  The search returned files which appeared to be 'close' in name, but not exact.  Also, the version numbers do not seem to appear.   

1)  Are these three files in Breezy already?
2)  Are there any risks in downloading these specific dependencies if they should replace earlier versions?

Thanks

---

### Post by Ramses de Norre on 2006-03-06
Are you compiling from source?

---

### Post by interse on 2006-03-06
The program file is a compressed tar file, so I believe the answer is yes, I am compiling from source.  I do know how to secure the 3 files needed, but I suspect that they are already on my system.

---

### Post by Ramses de Norre on 2006-03-06
Running this in the source directory should install all dependencies: ```
sudo -s
apt-get install auto-apt
auto-apt update
auto-apt updatedb
auto-apt update-local
auto-apt run ./configure
./configure
apt-get install checkinstall
checkinstall -D make install

```

---

### Post by interse on 2006-03-06
auto-apt is new to me, though apt-get is not.

I need a bit more clarification.  In its own directory (source directory), I first unzip the tar file? Then I run auto-apt?    

I need a bit more detail, use the following file  'examplefile.tar.gz'

Thank you for the further clarification.

---

### Post by knalle on 2006-03-06
```

tar zxvf examplefile.tar.gz
cd examplefile
make install

```

---

### Post by Ramses de Norre on 2006-03-06
You mostly need to run at least ./configure before make install (that's where auto-apt comes to help) and I'd advice to use checkinstall so you can easlily uninstall the program.

Just read the read me file and use auto-apt like I showed to run ./configure (do all the update steps first!).
Then run any make command they give you in the read me and then use checkinstall to install it.

---

### Post by interse on 2006-03-06
Thank you to all of you.  Your help was greatly appreciated.
Now I am trying to understand the process.

Here is the actual program I was trying to install:  [http://rightside.fissure.org/sudoku/](http://rightside.fissure.org/sudoku/)

Its dependencies are listed as: Python v. 2.3+, GTK v. 2.6+ and PyGTK v. 2.6+.

Here is what I did:   
    I did not download the dependencies as I suspected that they were already on my system.
    I extracted the tar.gz file
AND
    it created two folders, as I recall, and within one of the folders there was an executable file.  Using the Applications Editor, I created a path to the executable file and as the saying goes, "the rest was history."    
    I am curious, however.  I did not have to configure anything and it would appear that I was right in assuming that the three dependencies files were already on Breezy.  
    So my question remains, why could I not find these files exactly as listed above?  I used search for files and as I noted before, did find files that appeared to be very close in name.  

Thanks again.

---

