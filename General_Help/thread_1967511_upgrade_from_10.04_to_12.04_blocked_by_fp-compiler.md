---
title: "upgrade from 10.04 to 12.04 blocked by fp-compiler"
date: 2012-04-28
forum: General Help
---

### Post by wshackle on 2012-04-28
Just some history in case you need it 
I could never get the update-manager to offer the upgrade to 12.04 so I tried 

sudo  do-release-upgrade -d

after a couple of hours downloading it is stuck 

it says :

Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring fp-compiler-2.4.4 &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; FPC supports now multiple version installations. This allows              &#8593;  
 &#9474; co-existence of multiple versions on the same system. The default         &#9646;  
 &#9474; version can be selected using the update-alternatives command for the     &#9618;  
 &#9474; following groups:                                                         &#9618;  
 &#9474;     1)fpc      : compiler default version                                 &#9618;  
 &#9474;     2)fpc.cfg  : configuration file default version                       &#9618;  
 &#9474;     3)fp-utils : helper tools default version                             &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; What ever version you may choose as default, the configuration files (2)  &#9618;  
 &#9474; are always backward compatible and it may be very safe to use the latest  &#9618;  
 &#9474; version for it.                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; In order to use alternatives system for system wide FPC configuration     &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                            

It won't respond after showing this message. The Enter keys, the number keys etc do
nothing and it is just stuck
It doesn't even look like an error message. I have no interest in a pascal compiler
so I don't care whether it installs the default or no pascal compiler.

---

### Post by lisati on 2012-04-28
Make sure the window is focussed by clicking on it, then use the tab key to select the option you want. Hopefully this will help you get past this screen.

---

