---
title: "Lapackpp linking problem"
date: 2012-04-05
forum: General Help
---

### Post by perfectconan on 2012-04-05
I am new to g++ and lapack, and attempting to use them. I encountered a problem when I tried to compile the following naive code
  
#include <lapackpp.h> int main() {     LaGenMatDouble A;     return 0; }   

If I run the command 
  
$g++ -L/usr/local/lib -llapackpp test2.cpp    

where test2.cpp is the name of the cpp file, the terminal would give an error: 
  
test2.cpp:1:22: fatal error: lapackpp.h: No such file or directory 
   
BTW, if I run the command   
  
$pkg-config lapackpp --libs   the result is   

-L/usr/local/lib -llapackpp    

Could you please help me solve this? Thanks in advance!

---

