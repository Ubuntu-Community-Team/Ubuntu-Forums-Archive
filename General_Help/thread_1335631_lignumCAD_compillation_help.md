---
title: "lignumCAD compillation help"
date: 2009-11-23
forum: General Help
---

### Post by jtsmith73 on 2009-11-23
Hello,

I have an AMD64 system and I'm running into problems attempting to compile lignumCAD, a 32 bit program.  I thought I could compile it from source and it would work out okay, but it's failing compile.  I followed the easy compiling howto in order to acquire the necessary compilers for the system.  Since this source utilizes QT (according to the directions), I also installed qt3-dev-tools and qt4-qmake.  I can run the qmake without issues, but make outputs the following:

jimbo@Mobilebeast5:/opt/lignumCAD/lignumCAD-0.2/lignumCAD$ sudo qmake lignumCAD.pro
jimbo@Mobilebeast5:/opt/lignumCAD/lignumCAD-0.2/lignumCAD$ sudo make               
g++ -c -pipe -g -Wall -W -O0 -D_REENTRANT  -DOGLFT_NO_SOLID -DGL2PS_USE_QT -DGL2PS_USE_EMF -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_NO_DEBUG -I/usr/share/qt3/mkspecs/default -I. -Ilcfilechooser -Ilcfontchooser -Ilccolorchooser -Ilcdefaultfilechooser -Ilcdefaultcombobox -Ilcdefaultlengthspinbox -Ilcdefaultratiospinbox -Ilcconstraintchooser -Ilcdefaultspinbox -Ilcdefaultlengthconstraint -I. -I/usr/local/include/freetype2 -I/usr/local/src/Mesa/include -I/usr/include/X11/Xft -I/usr/local/include/OpenCASCADE -I/usr/include/qt3 -I.ui/ -I.moc/ -o .obj/main.o main.cpp                                              
In file included from /usr/include/qt3/qdragobject.h:50,                                                                                                     
                 from constants.h:29,                                                                                                                        
                 from main.cpp:39:                                                                                                                           
/usr/include/qt3/qimage.h: In member function ‘bool QImageTextKeyLang::operator<(const QImageTextKeyLang&) const’:                                           
/usr/include/qt3/qimage.h:61: warning: suggest parentheses around ‘&&’ within ‘||’                                                                           
In file included from constants.h:33,                                                                                                                        
                 from main.cpp:39:                                                                                                                           
ratio.h: At global scope:                                                                                                                                    
ratio.h:88: warning: type qualifiers ignored on function return type                                                                                         
In file included from main.cpp:39:                                                                                                                           
constants.h: In function ‘QString lC::Render::styleText(lC::Render::Style)’:                                                                                 
constants.h:254: warning: enumeration value ‘PARENT’ not handled in switch                                                                                   
constants.h:254: warning: enumeration value ‘HIGHLIGHTS’ not handled in switch                                                                               
constants.h: In function ‘QString lC::Edge::styleText(lC::Edge::Style)’:                                                                                     
constants.h:318: warning: enumeration value ‘SOLID’ not handled in switch                                                                                    
In file included from command.h:31,                                                                                                                          
                 from main.cpp:43:                                                                                                                           
vectoralgebra.h: At global scope:                                                                                                                            
vectoralgebra.h:68: error: expected initializer before ‘&’ token                                                                                             
vectoralgebra.h:162: error: expected initializer before ‘&’ token                                                                                            
vectoralgebra.h:256: error: expected initializer before ‘&’ token                                                                                            
vectoralgebra.h:350: error: expected initializer before ‘&’ token                                                                                            
vectoralgebra.h:566: error: expected initializer before ‘&’ token                                                                                            
constants.h:48: warning: ‘lC::MINIMUM_DIMESION’ defined but not used                                                                                         
make: *** [.obj/main.o] Error 1


I've never compiled anything using qmake or qt for that matter.  It's safe to say I'm lost and I need help.

Thanks in advance,

Jimbo

---

