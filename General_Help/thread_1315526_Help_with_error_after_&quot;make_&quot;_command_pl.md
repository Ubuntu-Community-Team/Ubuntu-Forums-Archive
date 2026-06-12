---
title: "Help with error after &quot;make &quot; command please"
date: 2009-11-05
forum: General Help
---

### Post by MrGrumpyArse on 2009-11-05
Hi, I am a new linux user running Ubuntu 9.10 Karmic.

I am trying to install ktorrent 3.3rc1 (for a particular plugin only contained in that release) from a downloaded .tar.bz2.  I have previously had this program installed successfully from the same download, but at the time i was running Kubuntu on top of my Ubuntu / gnome, which i have since removed.

I am following the same instructions as previously -

tar -xvjf ktorrent-3.X.Y.tar.bz2
cd ktorrent-3.X.Y
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
make
sudo make install

Everything goes fine with no errors recorded up to and including - 

cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..

But then when I enter the "make" command i get the following in terminal -

[  0%] Built target btcore_automoc
[  0%] Building CXX object libbtcore/CMakeFiles/btcore.dir/util/sha1hashgen.o
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:22:20: error: QtCrypto: No such file or directory
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:38: error: ‘Initializer’ in namespace ‘QCA’ does not name a type
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp: In constructor ‘bt::SHA1HashGen::SHA1HashGen()’:
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:44: error: ‘isSupported’ is not a member of ‘QCA’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:45: error: ‘isSupported’ is not a member of ‘QCA’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:51: error: invalid use of incomplete type ‘struct QCA::Hash’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.h:29: error: forward declaration of ‘struct QCA::Hash’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:53: error: invalid use of incomplete type ‘struct QCA::Hash’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.h:29: error: forward declaration of ‘struct QCA::Hash’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp: In destructor ‘bt::SHA1HashGen::~SHA1HashGen()’:
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:60: warning: possible problem detected in invocation of delete operator:
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:60: warning: invalid use of incomplete type ‘struct QCA::Hash’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.h:29: warning: forward declaration of ‘struct QCA::Hash’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:60: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp: In member function ‘bt::SHA1Hash bt::SHA1HashGen::generate(const bt::Uint8*, bt::Uint32)’:
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:67: error: invalid use of incomplete type ‘struct QCA::Hash’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.h:29: error: forward declaration of ‘struct QCA::Hash’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:67: error: ‘MemoryRegion’ is not a member of ‘QCA’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:68: error: invalid use of incomplete type ‘struct QCA::Hash’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.h:29: error: forward declaration of ‘struct QCA::Hash’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp: In member function ‘void bt::SHA1HashGen::update(const bt::Uint8*, bt::Uint32)’:
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:238: error: invalid use of incomplete type ‘struct QCA::Hash’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.h:29: error: forward declaration of ‘struct QCA::Hash’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:238: error: ‘MemoryRegion’ is not a member of ‘QCA’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp: In member function ‘bt::SHA1Hash bt::SHA1HashGen::get() const’:
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.cpp:376: error: invalid use of incomplete type ‘struct QCA::Hash’
/home/mark/Downloads/ktorrent-3.3rc1/libbtcore/util/sha1hashgen.h:29: error: forward declaration of ‘struct QCA::Hash’
make[2]: *** [libbtcore/CMakeFiles/btcore.dir/util/sha1hashgen.o] Error 1
make[1]: *** [libbtcore/CMakeFiles/btcore.dir/all] Error 2
make: *** [all] Error 2

Could anyone help explain the above error and possibly tell me how to fix it?

Any help would be much appreciated

Regards MrGrumpyArse / Mark

---

### Post by sedawk on 2009-11-05
First guess would be that because of this error line
> 
error: QtCrypto: No such file or directory

you are missing headers for Qt4 so you can
run qt4 software, but you cannot compile it.
Check if you missed to install any "dev" packages
related to qt4.
(Normally they should be automatically installed when installing
 headers for kde4. So you might also be missing kde4 headers)

---

### Post by alphaniner on 2009-11-05
A search for 'qtcrypto' at packages.ubuntu.com yielded [this]("http://packages.ubuntu.com/karmic/libqca2-dev").

---

### Post by MrGrumpyArse on 2009-11-05
Thanks for your replies...

Alphaniner
I searched in synaptic and the packages listed in the link  ie libqca2-dev libqca2, libqt4-dev where already installed but libqca2-doc wasnt.  I installed it and tried again but same error.


Sedawk
Sorry im very new to this so im not sure im following your instructions correctly but i searched in synaptic for qt4 packages with a dev extension and installed  - libavahi-qt4-dev and libavahi-qt4-1, but again same error.

I can remember previously that I had installed "a package" which gave me a "programming" entry in my applications list in my original straight ubuntu gnome install.  This disappeared when Kubuntu was later installed and then removed.  It has however now reappeared  with the installation of  libavahi-qt4-dev and libavahi-qt4-1, but has much less Apps within it.

Not sure as i say im very new to Linux and am just groping in the dark , so to speak.

Anymore suggestions or clarification would be much appreciated

Mark

---

### Post by alphaniner on 2009-11-05
This is a shot in the dark, but you might try installing libgcrypt11-dev.
I found it searching synaptic for 'sha1' because the errors all occured when trying to build 'CXX object libbtcore/CMakeFiles/btcore.dir/util/**sha1**hashgen.o'

And you do have 'build-essential' installed, right?

---

### Post by MrGrumpyArse on 2009-11-05
Yeah, both libgcrypt11-dev and build-essential are already installed.  Probably were added a few days ago when I followed a guide on these forums to build / install the latest ffmpeg/x264 so i could convert some .DTS audio to .aac.

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

The annoying thing is the first time round i had errors prior to the "make" stage which i managed to resolve by adding the packages that were suggest in the terminal error messages, or by searching the errors in google.  Once at the make stage everything went smoothly :?

Just to check after installing additional packages should i start the build (if thats the correct term) from scratch or is it ok just to continue from the make command?

The only other point of reference i have is from the ktorrent site where under the instructions it states -

You will need to install cmake and all the necessary development packages (Qt,KDE,libgmp,QCA2), to get it compiled properly.

I "think" ive done that but its all new to me, so i may have made some elementary mistake...

Thanks again 

ps
Im not giving in yet, im sure i must be learning lots that might make sense oneday

---

### Post by MrGrumpyArse on 2009-11-05
Well would you believe it ???

I decided to reboot my system and start again from scratch, this time it seems to have worked!  \\:D/

Havent yet tested the new ktorrent other than to launch it, but it appears to be there and working and still configured how i had it previously ie. correct download folders etc, and more importantly the "shut down when download completes" plug in is now showing, as this was the reason for the update in the first place.  Now if my internet provider didnt have daily upload limits I would never have to use it, but now at least its there when needed.....

Thanks again for all previous advice

Regards

MrGrumpyArse

---

### Post by vrm on 2009-12-11
I had the same problem,  I was able to get it to install by:

Opening '/ktorrent-3.3.1/libbtcore/util/sha1hashgen.cpp' and  '/usr/include/QtCrypto/qpipe.h' and changing '#include <QtCrypto>' to '#include </usr/include/QtCrypto/QtCrypto>' in both files.

I hope this helps anyone having a similar problem.

vrm.

---

