---
title: "Problems installing ia32-libs"
date: 2012-01-29
forum: General Help
---

### Post by midden on 2012-01-29
Hi all. After a year of holding on to Ubuntu 10.10 for dear life, I finally decided to reinstall with Xubuntu 11.10. After a brief period of re-orientation, I am happy with the new system, although a few issues remain. 

One of the problems I just ran into is that in order to run 32-bit programs I need to install ia32-libs; however, when I try to do that using aptitude, there is a host of unmet or broken dependencies:

```
The following NEW packages will be installed:
  gcc-4.6-base{a} ia32-libs ia32-libs-multiarch{a} lib32asound2{a} 
  lib32bz2-1.0{a} lib32ffi6{a} lib32gcc1{a} lib32ncurses5{a} 
  lib32stdc++6{a} lib32z1{a} libacl1{a} libattr1{a} libaudio2{a} 
  libavahi-client3{a} libavahi-common-data{a} libavahi-common3{a} libc6{a} 
  libcomerr2{a} libcups2{a} libcupsimage2{a} libcurl3{a} libdb5.1{a} 
  libdbus-1-3{a} libdrm-intel1{a} libdrm-nouveau1a{a} libdrm-radeon1{a} 
  libdrm2{a} libexpat1{a} libffi6{a} libfontconfig1{a} libfreetype6{a} 
  libgcc1{a} libgcrypt11{a} libgdbm3{a} libgl1-mesa-dri{a} 
  libgl1-mesa-glx{a} libglapi-mesa{a} libglib2.0-0{a} libglib2.0-data{a} 
  libgnutls26{a} libgpg-error0{a} libgssapi-krb5-2{a} libice6{a} 
  libidn11{a} libjpeg62{a} libk5crypto3{a} libkeyutils1{a} libkrb5-3{a} 
  libkrb5support0{a} liblcms1{a} libldap-2.4-2{a} libllvm2.9{a} libmng1{a} 
  libmysqlclient16{ab} libnspr4{a} libnss3{a} libpciaccess0{a} libpcre3{a} 
  libpng12-0{a} libqt4-dbus{a} libqt4-declarative{a} libqt4-designer{a} 
  libqt4-network{a} libqt4-opengl{a} libqt4-qt3support{a} libqt4-script{a} 
  libqt4-scripttools{a} libqt4-sql{a} libqt4-sql-mysql{a} libqt4-svg{a} 
  libqt4-test{a} libqt4-xml{a} libqt4-xmlpatterns{a} libqtcore4{a} 
  libqtgui4{a} librtmp0{a} libsasl2-2{a} libsasl2-modules{a} libselinux1{a} 
  libsm6{a} libsqlite3-0{a} libssl1.0.0{a} libstdc++6{a} libtasn1-3{a} 
  libtiff4{a} libuuid1{a} libx11-6{a} libxau6{a} libxcb1{a} libxdamage1{a} 
  libxdmcp6{a} libxext6{a} libxfixes3{a} libxi6{a} libxrender1{a} 
  libxss1{a} libxt6{a} libxxf86vm1{a} zlib1g{a} 
0 packages upgraded, 99 newly installed, 0 to remove and 0 not upgraded.
Need to get 72.3 MB of archives. After unpacking 252 MB will be used.
The following packages have unmet dependencies:
  libmysqlclient16: Conflicts: libmysqlclient16 but 5.1.58-1ubuntu1 is to be installed.
  libmysqlclient16: Depends: mysql-common (>= 5.1.58-1ubuntu1) which is a virtual package.
                    Conflicts: libmysqlclient16 but 5.1.58-1ubuntu1 is installed.
The following actions will resolve these dependencies:

      Keep the following packages at their current version:                     
1)      ia32-libs-multiarch [Not Installed]                                     
2)      libacl1 [Not Installed]                                                 
3)      libattr1 [Not Installed]                                                
4)      libaudio2 [Not Installed]                                               
5)      libavahi-client3 [Not Installed]                                        
6)      libavahi-common3 [Not Installed]                                        
7)      libc6 [Not Installed]                                                   
8)      libcomerr2 [Not Installed]                                              
9)      libcups2 [Not Installed]                                                
10)     libcupsimage2 [Not Installed]                                           
11)     libcurl3 [Not Installed]                                                
12)     libdb5.1 [Not Installed]                                                
13)     libdbus-1-3 [Not Installed]                                             
14)     libdrm-intel1 [Not Installed]                                           
15)     libdrm-nouveau1a [Not Installed]                                        
16)     libdrm-radeon1 [Not Installed]                                          
17)     libdrm2 [Not Installed]                                                 
18)     libexpat1 [Not Installed]                                               
19)     libffi6 [Not Installed]                                                 
20)     libfontconfig1 [Not Installed]                                          
21)     libfreetype6 [Not Installed]                                            
22)     libgcc1 [Not Installed]                                                 
23)     libgcrypt11 [Not Installed]                                             
24)     libgdbm3 [Not Installed]                                                
25)     libgl1-mesa-dri [Not Installed]                                         
26)     libgl1-mesa-glx [Not Installed]                                         
27)     libglapi-mesa [Not Installed]                                           
28)     libglib2.0-0 [Not Installed]                                            
29)     libgnutls26 [Not Installed]                                             
30)     libgpg-error0 [Not Installed]                                           
31)     libgssapi-krb5-2 [Not Installed]                                        
32)     libice6 [Not Installed]                                                 
33)     libidn11 [Not Installed]                                                
34)     libjpeg62 [Not Installed]                                               
35)     libk5crypto3 [Not Installed]                                            
36)     libkeyutils1 [Not Installed]                                            
37)     libkrb5-3 [Not Installed]                                               
38)     libkrb5support0 [Not Installed]                                         
39)     liblcms1 [Not Installed]                                                
40)     libldap-2.4-2 [Not Installed]                                           
41)     libllvm2.9 [Not Installed]                                              
42)     libmng1 [Not Installed]                                                 
43)     libmysqlclient16 [Not Installed]                                        
44)     libnspr4 [Not Installed]                                                
45)     libnss3 [Not Installed]                                                 
46)     libpciaccess0 [Not Installed]                                           
47)     libpcre3 [Not Installed]                                                
48)     libpng12-0 [Not Installed]                                              
49)     libqt4-dbus [Not Installed]                                             
50)     libqt4-declarative [Not Installed]                                      
51)     libqt4-designer [Not Installed]                                         
52)     libqt4-network [Not Installed]                                          
53)     libqt4-opengl [Not Installed]                                           
54)     libqt4-qt3support [Not Installed]                                       
55)     libqt4-script [Not Installed]                                           
56)     libqt4-scripttools [Not Installed]                                      
57)     libqt4-sql [Not Installed]                                              
58)     libqt4-sql-mysql [Not Installed]                                        
59)     libqt4-svg [Not Installed]                                              
60)     libqt4-test [Not Installed]                                             
61)     libqt4-xml [Not Installed]                                              
62)     libqt4-xmlpatterns [Not Installed]                                      
63)     libqtcore4 [Not Installed]                                              
64)     libqtgui4 [Not Installed]                                               
65)     librtmp0 [Not Installed]                                                
66)     libsasl2-2 [Not Installed]                                              
67)     libsasl2-modules [Not Installed]                                        
68)     libselinux1 [Not Installed]                                             
69)     libsm6 [Not Installed]                                                  
70)     libsqlite3-0 [Not Installed]                                            
71)     libssl1.0.0 [Not Installed]                                             
72)     libstdc++6 [Not Installed]                                              
73)     libtasn1-3 [Not Installed]                                              
74)     libtiff4 [Not Installed]                                                
75)     libuuid1 [Not Installed]                                                
76)     libx11-6 [Not Installed]                                                
77)     libxau6 [Not Installed]                                                 
78)     libxcb1 [Not Installed]                                                 
79)     libxdamage1 [Not Installed]                                             
80)     libxdmcp6 [Not Installed]                                               
81)     libxext6 [Not Installed]                                                
82)     libxfixes3 [Not Installed]                                              
83)     libxi6 [Not Installed]                                                  
84)     libxrender1 [Not Installed]                                             
85)     libxss1 [Not Installed]                                                 
86)     libxt6 [Not Installed]                                                  
87)     libxxf86vm1 [Not Installed]                                             
88)     zlib1g [Not Installed]                                                  

      Leave the following dependencies unresolved:                              
89)     ia32-libs recommends ia32-libs-multiarch                                
90)     libqt4-sql recommends libqt4-sql-mysql | libqt4-sql-odbc | libqt4-sql-ps


Accept this solution? [Y/n/q/?]
```

I always tread carefully when I see nearly 100 packages being installed along with un-met dependencies. Any suggestions on how to proceed?

Thanks for your help.

midden

---

### Post by midden on 2012-02-04
After not getting any responses, I decided to re-install Xubuntu (figuring that I had somehow botched the upgrade). This time, no problem installing acroread and other programs that require ia32-libs. Of course, when I went to install liother programs that require ia32bgdal1-dev I was prompted to remove ia32-libs and everything that depended on it.

This time, I decided to try apt-get instead of aptitude and was presented with a more reasonable solution. Weird, but it worked for me.

midden.

---

