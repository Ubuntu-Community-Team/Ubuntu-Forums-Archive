---
title: "Repository Errors"
date: 2011-03-10
forum: General Help
---

### Post by Morgen on 2011-03-10
I am having issues with a couple of repositories, Google and Dropbox specifically. Not sure if the problem is the same for both but "sudo apt-get update" gives me the following output (I removed the unrelated sections):

> Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg
Get:2 [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg                                                                 
Get:3 [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en                                             
Get:4 [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en                                                 
99% [3 Translation-en bzip2 0B] [Connecting to us.archive.ubuntu.com] [Waiting for headers] [Connecting to security.bzip2: (stdin) is not a bzip2 file.
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en                                               
Get:5 [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US                                          
Get:6 [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en_US                                              
82% [4 Translation-en bzip2 0B] [Connecting to us.archive.ubuntu.com] [Waiting for headers] [Connecting to security.bzip2: (stdin) is not a bzip2 file.
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en                                                   
66% [5 Translation-en_US bzip2 0B] [Connecting to us.archive.ubuntu.com] [Waiting for headers] [Connecting to securibzip2: (stdin) is not a bzip2 file.
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US                                            
49% [6 Translation-en_US bzip2 0B] [Connecting to us.archive.ubuntu.com] [Waiting for headers] [Connecting to securibzip2: (stdin) is not a bzip2 file.
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en_US                                                
Get:7 [http://dl.google.com](http://dl.google.com) stable Release                                                                           
Get:8 [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release                                                                     
Ign [http://dl.google.com](http://dl.google.com) stable Release                                                                             
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release                                                                       
Get:9 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                
54% [9 Packages bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Wbzip2: (stdin) is not a bzip2 file.
Err [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                  
  Sub-process /bin/bzip2 returned an error code (2)
Get:10 [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Sources                                                               
59% [10 Sources bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Wbzip2: (stdin) is not a bzip2 file.
Err [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Sources                                                                  
  Sub-process /bin/bzip2 returned an error code (2)
Get:11 [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages                                                         
63% [11 Packages bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Err [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages                                                            
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 54.1kB in 6s (8,575B/s)                                                                                     
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.bz2](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/main/source/Sources.bz2](http://linux.dropbox.com/ubuntu/dists/maverick/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/main/binary-i386/Packages.bz2](http://linux.dropbox.com/ubuntu/dists/maverick/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.


I have tried the following solutions with no luck:

[http://ubuntuforums.org/showthread.php?t=1240542&highlight=google+gpg+error+nodata](http://ubuntuforums.org/showthread.php?t=1240542&highlight=google+gpg+error+nodata)
[http://www.webupd8.org/2010/12/import-missing-gpg-keys-even-behind.html](http://www.webupd8.org/2010/12/import-missing-gpg-keys-even-behind.html)

Thanks for any help or ideas.

---

