---
title: "sudo apt-get update wont work (error)"
date: 2011-11-03
forum: General Help
---

### Post by Acutical on 2011-11-03
```
acutical@Ronnie-PC:~$ sudo apt-get update
Ign http://archive.ubuntu.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease
Hit http://archive.ubuntu.com oneiric Release.gpg
Hit http://extras.ubuntu.com oneiric Release.gpg
Hit http://archive.ubuntu.com oneiric Release
Hit http://extras.ubuntu.com oneiric Release    
Get:1 http://archive.ubuntu.com oneiric/universe Sources [4,677 kB]
Hit http://extras.ubuntu.com oneiric/main Sources       
Hit http://extras.ubuntu.com oneiric/main i386 Packages 
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Hit http://archive.ubuntu.com oneiric/main Sources                             
Hit http://archive.ubuntu.com oneiric/multiverse Sources                       
Hit http://archive.ubuntu.com oneiric/restricted Sources                       
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages                 
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://archive.ubuntu.com oneiric/main TranslationIndex                    
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex              
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex              
99% [1 Sources bzip2 0 B] [Waiting for headers]                     134 kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Hit http://archive.ubuntu.com oneiric/universe TranslationIndex                
Hit http://archive.ubuntu.com oneiric/main Translation-en                      
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en                
Hit http://archive.ubuntu.com oneiric/restricted Translation-en                
Hit http://archive.ubuntu.com oneiric/universe Translation-en                  
Fetched 4,677 kB in 45s (104 kB/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
acutical@Ronnie-PC:~$ 

```

Please help me :(

---

### Post by pavi_elex on 2011-11-04
replace /apt directory in /etc with fresh one.

---

