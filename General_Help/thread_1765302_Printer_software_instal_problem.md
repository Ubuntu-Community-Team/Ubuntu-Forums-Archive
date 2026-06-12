---
title: "Printer software instal problem"
date: 2011-05-22
forum: General Help
---

### Post by Dave T on 2011-05-22
New harddrive AMD 1800+. Installed Ubuntu 11.04 no probs. Debian drivers for Canon MP610 printer-scanner failed to install. Message on screen said,"Package has un-met dependencies, "cnijfilter-common", neads libcupsys2 (>=1.2.1). Installed 1.4.6-5 ubuntu 1(libcups2). (My comment;Package libcupsys2 not in path or missing, from a "windows" point-of-view!). Help!:confused:

---

### Post by demonipuch on 2011-05-26
Hello

I've written a little script that fix the dependency issue with libcupsys2. It modifies the control file in the .deb package to add a dependency with libcups2 which replaces libcupsys2 since Ubuntu 9.10 and it rebuilds the package. It also force installation on 64 bits systems (you need to install ia32-libs before if not already present in your system).

Open a terminal and download it :
```
wget http://demonipuch.free.fr/download/rebuildeb_canon.sh
```Set permission :
```
chmod +x rebuild_canon.sh
```Run the script :
```
./rebuild_canon.sh /path/to/file/cnijfilter-xxxxx_xxxxx_i386.deb
```Let me know if it worked.

---

### Post by Dave T on 2011-05-27
Yes,thanks. I understand the code you've given me, and will keep you informed. My latest effort resulted in an error message saying,"Unmet dependencies - broken cache". So before I go any further I am installing another DDR400 1 Gig memory module, after which I will run your code and then do the printer software install. Cheers from Dave.

---

### Post by Dave T on 2011-05-28
Hello demonipuch, downloaded "rebuildeb_canon.sh" to Downloads folder. Attempted to copy file to new CD-R disc without success; kept getting "disc is READ ONLY" message. Visual inspection shows disc was written to but disc shows no contents. Opened Downloads folder containing .deb drivers and rebuild file, opened TERM and entered your code in sequence, ran "./rebuild_canon.sh /path/to/file/cnijfilter-xxxxx-xxxxx-i386.deb and got error message saying something similar to incorrect path, no file found. I'm seriously interested in running a Ubuntu 11.04 system but so far the system I downloaded and installed to new H.D. has proven highly problematic and virtually useless. Very depressing to me. I was hoping to find sed and awk and resume reading c++. Man, I can't even get my printer to install! I follow your advice very carefully. from Dave T.

---

### Post by demonipuch on 2011-05-28
Hello

Can you please post the result of these commands :
```
ls -l ~/Downloads cnijfilter*
ls -l ~/Downloads rebuildeb.sh
```

---

### Post by Dave T on 2011-05-29
Hello demonipuch, Did it from TERM (alt-F2). Selected "run in terminal". No output, window flashed on screen briefly. -p and -s switches failed; I even tried to add a time value to these switches without result. Expand Downloads shows (EMPTY). Select Downloads shows 5 files; 
cnijfilter-common_2.80-1_i386.deb
cnijfilter-mp610series_2.80-1_i386.deb
scangearmp-mp610series_1.10-1_i386.deb    (these 3 to be installed)
plus: libcups2_1.4.4-7_i386.deb
        rebuildeb_canon.sh
What I did from the beginning;
Using my XP3 computer I downloaded from Internet these files and onto CD-R.
Then on Ubuntu Computer I copied all 5 files to Downloads folder from CD drive.
        Using Software Centre I installed Gdebi  (recommended).
I right clicked on file in Downloads and "opened with' - Gdebi.
The files were found and installation progressed normally to Dependency error.
I broke apt repeatedly until I changed to Gdebi.
I repaired apt and removed the broken package before installing Gdebi
      Concerning my CD recording, I left it to Default. Most unsatisfactory result ! But still cannot figure-out  "disc read-only" message and Empty message, when disc had obviously been written to. sincerely, Dave T.

---

### Post by demonipuch on 2011-05-29
Hello

Open a terminal. Change directory to your Downloads folder. Run the script for each cnijfilter.deb file
```

cd Downloads
./rebuildeb_canon.sh cnijfilter-common_2.80-1_i386.deb
./rebuildeb_canon.sh  cnijfilter-mp610series_2.80-1_i386.deb
```The last package shouldn't need any modification. Just install it with dpkg :
```
sudo dpkg -i scangearmp-mp610series_1.10-1_i386.deb
```

---

### Post by Dave T on 2011-06-02
Deleted all files. Downloaded all again into Ubuntu system Downloads. Opened TERM on top of files and ran commands; got error msg "could not open location (command) error stating file (command) no such file or directory." Moved files to Desktop and repeated procedure with same result. Have contacted Canon to supply updated packages. Before I ran TERM I gave all the files full rwx permissions.
   Question: Why did the software engineers change libcupsys2 to libcups2? Surely they could have ensured backward compatibility with a few lines of embedded code?

---

### Post by Dave T on 2011-06-02
Canon Home just told me they do not support, or supply, open source .deb drivers for Canon MP610 printer/scanners. They do have old drivers on thier downloads site but they appear, and do not seem to care, to update them for Ubuntu .deb Linux users. My response is, Avoid buying a Canon Printer for your Ubuntu system as I virtually got told to +)&%#@!-off; politely. I was told by the salesman when I purchased the printer a few days ago,that,"Yes, current Linux drivers are available via the net from Canon". That is a False and fraudulent statement from Canon to make a sale. Be aware, buy another brand of printer.

---

### Post by Dave T on 2011-06-03
Admin: You may delete this thread. Thankyou to helper but none of the commands has worked. ls-l xxxxxxx failed, cd xxxxxxx failed. Gave myself and all packages +rwx across all domains to no good effect. Found TERM to be capable of opening Programs and nothing else. Kept getting WRONG PATH and FILE NOT FOUND errors.
I cannot compete with that. When I installed U 11.04 I created one account with pwd login, and thought I would have su powers but obviously not. Bye all.

---

### Post by Dave T on 2011-06-07
see other thread for full recipe as to how to get to and use the true c command line in Ubuntu 11.04. Cannot be bothered typing it twice, sorry. For new Ubuntu devotees, I would suggest Print out and Read. Cheers from Dave T.

---

