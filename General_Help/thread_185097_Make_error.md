---
title: "Make error"
date: 2006-05-31
forum: General Help
---

### Post by Deus- on 2006-05-31
When trying to make fluxbox after a successful ./configure
the next message comes:



make  all-recursive
make[1]: Entering directory `/home/fluxbox-0.1.14'
Making all in data
make[2]: Entering directory `/home/fluxbox-0.1.14/data'
Making all in styles
make[3]: Entering directory `/home/fluxbox-0.1.14/data/styles'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/data/styles'
make[3]: Entering directory `/home/fluxbox-0.1.14/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/data'
make[2]: Leaving directory `/home/fluxbox-0.1.14/data'
Making all in doc
make[2]: Entering directory `/home/fluxbox-0.1.14/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/fluxbox-0.1.14/doc'
Making all in nls
make[2]: Entering directory `/home/fluxbox-0.1.14/nls'
Making all in C
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/C'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/C'
Making all in da_DK
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/da_DK'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/da_DK'
Making all in es_ES
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/es_ES'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/es_ES'
Making all in et_EE
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/et_EE'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/et_EE'
Making all in fr_FR
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/fr_FR'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/fr_FR'
Making all in pt_BR
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/pt_BR'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/pt_BR'
Making all in ru_RU
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/ru_RU'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/ru_RU'
Making all in sv_SE
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/sv_SE'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/sv_SE'
Making all in tr_TR
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/tr_TR'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/tr_TR'
Making all in it_IT
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/it_IT'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/it_IT'
Making all in pt_PT
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/pt_PT'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/pt_PT'
Making all in bg_BG
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/bg_BG'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/bg_BG'
Making all in ja_JP
make[3]: Entering directory `/home/fluxbox-0.1.14Making all in lv_LV
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/lv_LV'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/lv_LV'
make[3]: Entering directory `/home/fluxbox-0.1.14/nls'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls'
make[2]: Leaving directory `/home/fluxbox-0.1.14/nls'
Making all in src
make[2]: Entering directory `/home/fluxbox-0.1.14/src'
Making all in FbTk
make[3]: Entering directory `/home/fluxbox-0.1.14/src/FbTk'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/src/FbTk'
make[3]: Entering directory `/home/fluxbox-0.1.14/src'
source='Basemenu.cc' object='Basemenu.o' libtool=no \
        depfile='.deps/Basemenu.Po' tmpdepfile='.deps/Basemenu.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        g++ -DHAVE_CONFIG_H -I. -I. -I..  -Wall -DLOCALEPATH=\"/usr/local/share/fluxbox/nls\" -DDEFAULTMENU=\"/usr/local/share/fluxbox/menu\" -DDEFAULTSTYLE=\"/usr/$
make[3]: Leaving directory `/home/fluxbox-0.1.14/src'
make[2]: Leaving directory `/home/fluxbox-0.1.14/src'
make[1]: Leaving directory `/home/fluxbox-0.1.14'/nls/ja_JP'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/ja_JP'
Making all in lv_LV
make[3]: Entering directory `/home/fluxbox-0.1.14/nls/lv_LV'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls/lv_LV'
make[3]: Entering directory `/home/fluxbox-0.1.14/nls'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/fluxbox-0.1.14/nls'
make[2]: Leaving directory `/home/fluxbox-0.1.14/nls'
Making all in src
make[2]: Entering directory `/home/fluxbox-0.1.14/src'
Making all in FbTk
make[3]: Entering directory `/home/fluxbox-0.1.14/src/FbTk'
source='Font.cc' object='Font.o' libtool=no \
        depfile='.deps/Font.Po' tmpdepfile='.deps/Font.TPo' \
        depmode=gcc3 /bin/sh ../../depcomp \
        g++ -DHAVE_CONFIG_H -I. -I. -I../..     -g -O2  -DSHAPE    -c -o Font.o `test -f Font.cc || echo './'`Font.cc
source='XmbFontImp.cc' object='XmbFontImp.o' libtool=no \
        depfile='.deps/XmbFontImp.Po' tmpdepfile='.deps/XmbFontImp.TPo' \
        depmode=gcc3 /bin/sh ../../depcomp \
        g++ -DHAVE_CONFIG_H -I. -I. -I../..     -g -O2  -DSHAPE    -c -o XmbFontImp.o `test -f XmbFontImp.cc || echo './'`XmbFontImp.cc
rm -f libFbTk.a
ar cru libFbTk.a App.o Color.o EventManager.o Font.o SignalHandler.o Texture.o XFontImp.o XmbFontImp.o 
ranlib libFbTk.amake[3]: Leaving directory `/home/fluxbox-0.1.14/src/FbTk'
make[3]: Entering directory `/home/fluxbox-0.1.14/src'
source='BaseDisplay.cc' object='BaseDisplay.o' libtool=no \
        depfile='.deps/BaseDisplay.Po' tmpdepfile='.deps/BaseDisplay.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        g++ -DHAVE_CONFIG_H -I. -I. -I..  -Wall -DLOCALEPATH=\"/usr/local/share/fluxbox/nls\" -DDEFAULTMENU=\"/usr/local/share/fluxbox/menu\" -DDEFAULTSTYLE=\"/usr/local/share/fluxbox/styles/Clean\" -DDEFAULTKEYSFILE=\"/usr/local/share/fluxbox/keys\" -DDEFAULT_INITFILE=\"/usr/local/share/fluxbox/init\" -IFbTk   -g -O2  -DSHAPE    -c -o BaseDisplay.o `test -f BaseDisplay.cc || echo './'`BaseDisplay.cc
Timer.hh:43: warning: â&#8364;&#732;class TimeoutHandlerâ&#8364;&#8482; has virtual functions but non-virtual destructor
BaseDisplay.cc: In function â&#8364;&#732;void bexec(const char*, char*)â&#8364;&#8482;:
BaseDisplay.cc:126: warning: missing sentinel in function call
source='Basemenu.cc' object='Basemenu.o' libtool=no \
        depfile='.deps/Basemenu.Po' tmpdepfile='.deps/Basemenu.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        g++ -DHAVE_CONFIG_H -I. -I. -I..  -Wall -DLOCALEPATH=\"/usr/local/share/fluxbox/nls\" -DDEFAULTMENU=\"/usr/local/share/fluxbox/menu\" -DDEFAULTSTYLE=\"/usr/local/share/fluxbox/styles/Clean\" -DDEFAULTKEYSFILE=\"/usr/local/share/fluxbox/keys\" -DDEFAULT_INITFILE=\"/usr/local/share/fluxbox/init\" -IFbTk   -g -O2  -DSHAPE    -c -o Basemenu.o `test -f Basemenu.cc || echo './'`Basemenu.cc
Resource.hh: In constructor â&#8364;&#732;Resource<T>::Resource(ResourceManager&, T, const std::string&, const std::string&)â&#8364;&#8482;:
Resource.hh:74: error: invalid use of undefined type â&#8364;&#732;struct ResourceManagerâ&#8364;&#8482;
Resource.hh:59: error: forward declaration of â&#8364;&#732;struct ResourceManagerâ&#8364;&#8482;
Resource.hh: In destructor â&#8364;&#732;virtual Resource<T>::~Resource()â&#8364;&#8482;:
Resource.hh:77: error: invalid use of undefined type â&#8364;&#732;struct ResourceManagerâ&#8364;&#8482;
Resource.hh:59: error: forward declaration of â&#8364;&#732;struct ResourceManagerâ&#8364;&#8482;
Timer.hh: At global scope:
Timer.hh:43: warning: â&#8364;&#732;class TimeoutHandlerâ&#8364;&#8482; has virtual functions but non-virtual destructor
Toolbar.hh:173: warning: â&#8364;&#732;class Toolbar::HideHandlerâ&#8364;&#8482; has virtual functions but non-virtual destructor
FbTk/SignalHandler.hh:32: warning: â&#8364;&#732;class FbTk::SignalEventHandlerâ&#8364;&#8482; has virtual functions but non-virtual destructor
make[3]: *** [Basemenu.o] Error 1
make[3]: Leaving directory `/home/fluxbox-0.1.14/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/fluxbox-0.1.14/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/fluxbox-0.1.14'
make: *** [all] Error 2
sh-3.00# make > make-err
Resource.hh: In constructor â&#8364;&#732;Resource<T>::Resource(ResourceManager&, T, const std::string&, const std::string&)â&#8364;&#8482;:
Resource.hh:74: error: invalid use of undefined type â&#8364;&#732;struct ResourceManagerâ&#8364;&#8482;
Resource.hh:59: error: forward declaration of â&#8364;&#732;struct ResourceManagerâ&#8364;&#8482;
Resource.hh: In destructor â&#8364;&#732;virtual Resource<T>::~Resource()â&#8364;&#8482;:
Resource.hh:77: error: invalid use of undefined type â&#8364;&#732;struct ResourceManagerâ&#8364;&#8482;
Resource.hh:59: error: forward declaration of â&#8364;&#732;struct ResourceManagerâ&#8364;&#8482;
Timer.hh: At global scope:
Timer.hh:43: warning: â&#8364;&#732;class TimeoutHandlerâ&#8364;&#8482; has virtual functions but non-virtual destructor
Toolbar.hh:173: warning: â&#8364;&#732;class Toolbar::HideHandlerâ&#8364;&#8482; has virtual functions but non-virtual destructor
FbTk/SignalHandler.hh:32: warning: â&#8364;&#732;class FbTk::SignalEventHandlerâ&#8364;&#8482; has virtual functions but non-virtual destructor
make[3]: *** [Basemenu.o] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error

and if 'make install' was tried after this nothing naturally worked

Any clue what is going on?:confused:
(/home directory is just an example...it did not work on any other directory either)

---

### Post by thumper on 2006-05-31
There is a bug in the code.

On line 59 of Resource.hh the class ResourceManager is forward declared.
On line 74 and line 77 the class is used.  You are not allowed to do this as the type is undefined.  Hence the errors.

---

### Post by Deus- on 2006-05-31
I assume there is no way to fix this than to download the source again?
Then it does the same thing again since I've tried it before...
And if I do it via apt-get install fluxbox (which presumes editing the sources.list) my linux system goes nuts...

---

### Post by thumper on 2006-05-31
What do you mean exactly by "goes nuts"?

I am a little surprised that the downloaded source had a problem...

---

### Post by Deus- on 2006-05-31
If I do the apt-get install fluxbox, next my system advices me to start apt-get -f install
and asks to remove software for about 700mb

---

### Post by D!mon on 2006-06-01
if you have a source tar.gz DO NOT type make and make install!!!
First, install a package checkinstall (sudo apt-get install checkinstall), and then when you want to install something from the source type ./configure and then checkinstall, this will create and install .deb package  so you will be able to remove installed package using aptitude or adept or synaptic i mean it will be installed 'correctly'

---

