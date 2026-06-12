---
title: "Itask-ng for Enlightenment"
date: 2009-09-12
forum: General Help
---

### Post by thecow on 2009-09-12
Hello I recently installed enlightenment on ubuntu 9.04.  I installed it myself,downloading the source code and the source of all the depedencies and installed them all.  I then booted into the Enlightenment environment and am trying to install itask-ng.

The problem is when its compiling it says this a few times
"[eina_array.c:520] eina_array_clean() *** Eina Magic Check Failed !!!           
    Input handle is wrong type                                                  
    Expected: 9876123b - Eina Array                                             
    Supplied: 00000000 - (null)                                                 
*** NAUGHTY PROGRAMMER!!!                                                       
*** SPANK SPANK SPANK!!!                                                        
*** Now go fix your code. Tut tut tut!                                          

[eina_array.c:520] eina_array_clean() *** Eina Magic Check Failed !!!
    Input handle is wrong type                                       
    Expected: 9876123b - Eina Array                                  
    Supplied: 00000000 - (null)                                      
*** NAUGHTY PROGRAMMER!!!                                            
*** SPANK SPANK SPANK!!!                                             
*** Now go fix your code. Tut tut tut!  
"


And by a few times I mean more like 10-20.


It still lets me run make install however so anyways I tried to load the module in.  When I try and load the module it gives me this error:

"There was an error loading module named itask-ng
The full path to this module is:
itask-ng/linux-gnu-i686-ver-svn-03/module.so

The error reported was:
/usr/local/lib/enlightenment/modules/itask-ng/linux-gnu-i686-ver-svn-03/module/so undefined symbol: e_widget_size_min_get"




Anyone have any ideas?

Also if this is the wrong place for this question please feel free to move it.

Thank you for the help

---

