---
title: "Rigs of rods cant run"
date: 2012-07-07
forum: General Help
---

### Post by louie123 on 2012-07-07
i just downloaded rigs of rods for ubuntu i tried installing the deb i get this error       Dependency is not satisfiable: socketw (>=0) also i download it a diffent way alsohttp://www.rigsofrods.com/wiki/pages/Compiling_Sources_under_Linuxrun it i downloaded the game from here [http://www.rigsofrods.com/wiki/pages/Compiling_Sources_under_Linux](http://www.rigsofrods.com/wiki/pages/Compiling_Sources_under_Linux) also i downloaded the needed compents for the game but how do i it i really want to play this game.

---

### Post by ubudog on 2012-07-08
Try going through [this]("http://www.rigsofrods.com/wiki/pages/Compiling_3rd_party_libraries") page, and compile all the needed libraries.  Then, try downloading their (**64-bit**) .deb from [here]("http://apt.rigsofrods.com/dists/lucid/main/binary-amd64/rigsofrods-unstable-amd64.deb") and installing it.

Post if you have any troubles compiling/installing anything.  :) 

Best of luck,
ubudog

---

### Post by louie123 on 2012-07-08
> **ubudog said:**
> Try going through [this]("http://www.rigsofrods.com/wiki/pages/Compiling_3rd_party_libraries") page, and compile all the needed libraries.  Then, try downloading their (**64-bit**) .deb from [here]("http://apt.rigsofrods.com/dists/lucid/main/binary-amd64/rigsofrods-unstable-amd64.deb") and installing it.

Post if you have any troubles compiling/installing anything.  :) 

Best of luck,
ubudog thanks but im redownloading the deb and reinstailling everything

---

### Post by louie123 on 2012-07-08
can somebody give me wxWidgets >= 2.6 the link  to install this its needed for ror also im using ubuntu 10.10  i really want to run this game

---

### Post by Rexilion on 2012-07-08
wxWidgets is provided with ubuntu. Maybe this will help?

> aptitude -s -R install wx2.6-headers

Otherwise, check [this page]("http://packages.ubuntu.com/search?keywords=wx&searchon=names&suite=precise&section=all") for other viable packages that will satisfy the required dependency.

---

### Post by louie123 on 2012-07-08
also when i install caelum i think i get an error ryan@ryan-Aspire-5532:~$ hg clone [https://caelum.googlecode.com/hg/](https://caelum.googlecode.com/hg/) caelum 
abort: destination 'caelum' is not empty
ryan@ryan-Aspire-5532:~$ cd caelum
ryan@ryan-Aspire-5532:~/caelum$ cmake .
-- Could NOT find Boost
found doxygen, generating documentation
-- Configuring done
-- Generating done
-- Build files have been written to: /home/ryan/caelum
ryan@ryan-Aspire-5532:~/caelum$ make -j8
[  4%] [  8%] [ 13%] Building CXX object main/CMakeFiles/Caelum.dir/src/Moon.o
Building CXX object main/CMakeFiles/Caelum.dir/src/BrightStarCatalogue.o
Building CXX object main/CMakeFiles/Caelum.dir/src/InternalUtilities.o
[ 17%] Building CXX object main/CMakeFiles/Caelum.dir/src/PrecipitationController.o
[ 21%] [ 26%] Building CXX object main/CMakeFiles/Caelum.dir/src/CameraBoundElement.o
[ 30%] Building CXX object main/CMakeFiles/Caelum.dir/src/SkyDome.o
[ 34%] Building CXX object main/CMakeFiles/Caelum.dir/src/TypeDescriptor.o
Building CXX object main/CMakeFiles/Caelum.dir/src/SkyLight.o
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:25: warning: ignoring #pragma warning 
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:28: warning: ignoring #pragma warning 
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/InternalUtilities.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/SkyLight.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/PrecipitationController.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/CameraBoundElement.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/TypeDescriptor.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/SkyDome.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/Moon.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/BrightStarCatalogue.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /home/ryan/caelum/main/include/InternalUtilities.h:25,
                 from /home/ryan/caelum/main/src/Moon.cpp:23:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
In file included from /home/ryan/caelum/main/include/SkyDome.h:27,
                 from /home/ryan/caelum/main/src/SkyDome.cpp:22:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
In file included from /home/ryan/caelum/main/include/PointStarfield.h:26,
                 from /home/ryan/caelum/main/src/BrightStarCatalogue.cpp:22:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
/home/ryan/caelum/main/src/CameraBoundElement.cpp:64: warning: unused parameter &#8216;radius&#8217;
In file included from /home/ryan/caelum/main/include/InternalUtilities.h:25,
                 from /home/ryan/caelum/main/src/InternalUtilities.cpp:23:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
In file included from /home/ryan/caelum/main/include/InternalUtilities.h:25,
                 from /home/ryan/caelum/main/src/PrecipitationController.cpp:23:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
/home/ryan/caelum/main/src/PrecipitationController.cpp:218: warning: unused parameter &#8216;pass_id&#8217;
/home/ryan/caelum/main/src/PrecipitationController.cpp:237: warning: unused parameter &#8216;pass_id&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
/home/ryan/caelum/main/src/BrightStarCatalogue.cpp:9145: warning: missing initializer for member &#8216;Caelum::BrightStarCatalogueEntry::magn&#8217;
[ 39%] [ 43%] [ 47%] [ 52%] [ 56%] [ 60%] [ 65%] Building CXX object main/CMakeFiles/Caelum.dir/src/FastGpuParamRef.o
Building CXX object main/CMakeFiles/Caelum.dir/src/FlatCloudLayer.o
Building CXX object main/CMakeFiles/Caelum.dir/src/GroundFog.o
Building CXX object main/CMakeFiles/Caelum.dir/src/CaelumPrecompiled.o
Building CXX object main/CMakeFiles/Caelum.dir/src/CaelumDefaultTypeDescriptorData.o
Building CXX object main/CMakeFiles/Caelum.dir/src/PointStarfield.o
Building CXX object main/CMakeFiles/Caelum.dir/src/CaelumPlugin.o
[ 69%] Building CXX object main/CMakeFiles/Caelum.dir/src/CloudSystem.o
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/CaelumPrecompiled.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/FastGpuParamRef.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/GroundFog.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/PointStarfield.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/CloudSystem.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/CaelumDefaultTypeDescriptorData.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/FlatCloudLayer.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/CaelumPlugin.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /home/ryan/caelum/main/include/InternalUtilities.h:25,
                 from /home/ryan/caelum/main/include/FlatCloudLayer.h:25,
                 from /home/ryan/caelum/main/src/CloudSystem.cpp:23:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
In file included from /home/ryan/caelum/main/include/PointStarfield.h:26,
                 from /home/ryan/caelum/main/src/PointStarfield.cpp:22:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
In file included from /home/ryan/caelum/main/include/ImageStarfield.h:26,
                 from /home/ryan/caelum/main/include/CaelumSystem.h:26,
                 from /home/ryan/caelum/main/src/CaelumDefaultTypeDescriptorData.cpp:27:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
In file included from /home/ryan/caelum/main/include/InternalUtilities.h:25,
                 from /home/ryan/caelum/main/include/FlatCloudLayer.h:25,
                 from /home/ryan/caelum/main/src/FlatCloudLayer.cpp:22:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
In file included from /home/ryan/caelum/main/include/GroundFog.h:26,
                 from /home/ryan/caelum/main/src/GroundFog.cpp:22:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
In file included from /home/ryan/caelum/main/src/CaelumDefaultTypeDescriptorData.cpp:27:
/home/ryan/caelum/main/include/CaelumSystem.h:645: warning: type qualifiers ignored on function return type
[ 73%] [ 78%] [ 82%] [ 86%] [ 91%] [ 95%] Building CXX object main/CMakeFiles/Caelum.dir/src/ImageStarfield.o
Building CXX object main/CMakeFiles/Caelum.dir/src/Sun.o
Building CXX object main/CMakeFiles/Caelum.dir/src/Astronomy.o
Building CXX object main/CMakeFiles/Caelum.dir/src/CaelumScriptTranslator.o
Building CXX object main/CMakeFiles/Caelum.dir/src/CaelumSystem.o
Building CXX object main/CMakeFiles/Caelum.dir/src/UniversalClock.o
[100%] Building CXX object main/CMakeFiles/Caelum.dir/src/DepthComposer.o
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/Sun.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/CaelumSystem.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/Astronomy.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/CaelumScriptTranslator.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/DepthComposer.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/ImageStarfield.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /usr/local/include/OGRE/OgreTextureUnitState.h:37,
                 from /usr/local/include/OGRE/OgreControllerManager.h:37,
                 from /usr/local/include/OGRE/Ogre.h:45,
                 from /home/ryan/caelum/main/include/CaelumPrecompiled.h:24,
                 from /home/ryan/caelum/main/src/UniversalClock.cpp:21:
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;name&#8217;
/usr/local/include/OGRE/OgreTexture.h:381: warning: unused parameter &#8216;pData&#8217;
In file included from /home/ryan/caelum/main/include/Sun.h:27,
                 from /home/ryan/caelum/main/src/Sun.cpp:22:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
In file included from /home/ryan/caelum/main/include/ImageStarfield.h:26,
                 from /home/ryan/caelum/main/src/ImageStarfield.cpp:22:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
In file included from /home/ryan/caelum/main/include/ImageStarfield.h:26,
                 from /home/ryan/caelum/main/include/CaelumSystem.h:26,
                 from /home/ryan/caelum/main/src/CaelumSystem.cpp:22:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
In file included from /home/ryan/caelum/main/src/CaelumSystem.cpp:22:
/home/ryan/caelum/main/include/CaelumSystem.h:645: warning: type qualifiers ignored on function return type
/home/ryan/caelum/main/src/DepthComposer.cpp:181: warning: unused parameter &#8216;pass_id&#8217;
/home/ryan/caelum/main/src/DepthComposer.cpp:211: warning: unused parameter &#8216;pass_id&#8217;
/home/ryan/caelum/main/src/DepthComposer.cpp:441: warning: unused parameter &#8216;rend&#8217;
/home/ryan/caelum/main/src/DepthComposer.cpp:441: warning: unused parameter &#8216;priority&#8217;
/home/ryan/caelum/main/src/DepthComposer.cpp:441: warning: unused parameter &#8216;pQueue&#8217;
In file included from /home/ryan/caelum/main/include/ImageStarfield.h:26,
                 from /home/ryan/caelum/main/include/CaelumSystem.h:26,
                 from /home/ryan/caelum/main/src/CaelumScriptTranslator.cpp:27:
/home/ryan/caelum/main/include/PrivatePtr.h:43: warning: type qualifiers ignored on function return type
In file included from /home/ryan/caelum/main/src/CaelumScriptTranslator.cpp:27:
/home/ryan/caelum/main/include/CaelumSystem.h:645: warning: type qualifiers ignored on function return type
/home/ryan/caelum/main/src/CaelumScriptTranslator.cpp:55: warning: unused parameter &#8216;createParams&#8217;
/home/ryan/caelum/main/src/CaelumSystem.cpp:648: warning: unused parameter &#8216;time&#8217;
/home/ryan/caelum/main/src/CaelumSystem.cpp:658: warning: unused parameter &#8216;time&#8217;
/home/ryan/caelum/main/src/CaelumSystem.cpp:669: warning: unused parameter &#8216;time&#8217;
/home/ryan/caelum/main/src/CaelumSystem.cpp:680: warning: unused parameter &#8216;time&#8217;
/home/ryan/caelum/main/src/CaelumSystem.cpp:697: warning: unused parameter &#8216;moonDir&#8217;
/home/ryan/caelum/main/src/CaelumSystem.cpp:755: warning: type qualifiers ignored on function return type
Linking CXX shared library ../lib/libCaelum.so
[100%] Built target Caelum
ryan@ryan-Aspire-5532:~/caelum$ sudo make install
[sudo] password for ryan: 

also i think i get a error for hydrax iwget [http://modclub.rigsofrods.com/xavi/hydrax-0.5.2-ogre-17-patched.tar.bz2](http://modclub.rigsofrods.com/xavi/hydrax-0.5.2-ogre-17-patched.tar.bz2)
tar xvfj hydrax*
cd hydrax-*
## Fix for errors running the make command: remove the # on the lines below up to the end
#cp makefile makefile.orig
#sed 's|PREFIX =/usr|PREFIX =/usr/local|g' makefile.orig > makefile
## end of fix
make -j2
sudo make install
cd ..ryan@ryan-Aspire-5532:~$ wget [http://modclub.rigsofrods.com/xavi/hydrax-0.5re-17-patched.tar.bz2](http://modclub.rigsofrods.com/xavi/hydrax-0.5re-17-patched.tar.bz2)
--2012-07-08 08:50:09--  [http://modclub.rigsofrods.com/xavi/hydrax-0.5.2-ogre-17-patched.tar.bz2](http://modclub.rigsofrods.com/xavi/hydrax-0.5.2-ogre-17-patched.tar.bz2)
Resolving modclub.rigsofrods.com... 178.63.196.194
Connecting to modclub.rigsofrods.com|178.63.196.194|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 699517 (683K) [application/x-bzip]
Saving to: `hydrax-0.5.2-ogre-17-patched.tar.bz2.1'

100%[======================================>] 699,517     18.6K/s   in 28s     

2012-07-08 08:50:38 (24.4 KB/s) - `hydrax-0.5.2-ogre-17-patched.tar.bz2.1' saved [699517/699517]

ryan@ryan-Aspire-5532:~$ tar xvfj hydrax*
tar (child): hydrax-0.5.2-ogre-17-patched: Cannot read: Is a directory
tar (child): At beginning of tape, quitting now
tar (child): Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error is not recoverable: exiting now
ryan@ryan-Aspire-5532:~$ cd hydrax-*
ryan@ryan-Aspire-5532:~/hydrax-0.5.2-ogre-17-patched$ ## Fix for errors running the make command: remove the # on the lines below up to the end
ryan@ryan-Aspire-5532:~/hydrax-0.5.2-ogre-17-patched$ #cp makefile makefile.origryan@ryan-Aspire-5532:~/hydrax-0.5.2-ogre-17-patched$ #sed 's|PREFIX =/usr|PREFIX =/usr/local|g' makefile.orig > makefile
ryan@ryan-Aspire-5532:~/hydrax-0.5.2-ogre-17-patched$ ## end of fix
ryan@ryan-Aspire-5532:~/hydrax-0.5.2-ogre-17-patched$ make -j2
mkdir -p obj
mkdir -p obj/Release
g++ -s -O2 -fPIC -c -I/usr/include/OGRE -I./include/ -o obj/Release/CfgFileManager.o src/CfgFileManager.cpp
mkdir -p obj/Release/Modules
mkdir -p obj/Release/Noise
mkdir -p obj/Release/Modules/ProjectedGrid
mkdir -p obj/Release/Modules/RadialGrid
mkdir -p obj/Release/Modules/SimpleGrid
mkdir -p obj/Release/Noise/FFT
mkdir -p obj/Release/Noise/Perlin
mkdir -p lib
mkdir -p lib/Release
g++ -s -O2 -fPIC -c -I/usr/include/OGRE -I./include/ -o obj/Release/DecalsManager.o src/DecalsManager.cpp
In file included from ./include/CfgFileManager.h:28,
                 from src/CfgFileManager.cpp:25:
./include/Prerequisites.h:29: fatal error: Ogre.h: No such file or directory
compilation terminated.
make: *** [obj/Release/CfgFileManager.o] Error 1
make: *** Waiting for unfinished jobs....
In file included from ./include/DecalsManager.h:28,
                 from src/DecalsManager.cpp:25:
./include/Prerequisites.h:29: fatal error: Ogre.h: No such file or directory
compilation terminated.
make: *** [obj/Release/DecalsManager.o] Error 1
ryan@ryan-Aspire-5532:~/hydrax-0.5.2-ogre-17-patched$ sudo make install
[sudo] password for ryan: 
mkdir -p /usr/lib
cp lib/Release/libhydrax.so.0.5.2 /usr/lib/libhydrax.so.0.5.2 
cp: cannot stat `lib/Release/libhydrax.so.0.5.2': No such file or directory
make: *** [InstLib] Error 1
 i really want to play this game i dont want to run thought wine when i load a addon ror in windows version with wine the game crashes if i run the linux version i shouldnt have no bugs  i really want to drive the thomas hdx [http://www.rigsofrods.com/repository/view/4499](http://www.rigsofrods.com/repository/view/4499)

---

### Post by louie123 on 2012-07-08
> **Rexilion said:**
> wxWidgets is provided with ubuntu. Maybe this will help?



Otherwise, check [this page]("http://packages.ubuntu.com/search?keywords=wx&searchon=names&suite=precise&section=all") for other viable packages that will satisfy the required dependency. thanks

---

### Post by louie123 on 2012-07-08
when i open rigsofrods-unstable-amd64.deb Dependency is not satisfiable: socketw (>= 0)  i want to get rid of this error so i can install it

---

### Post by Rexilion on 2012-07-08
Your build probably fails because you don't have boost installed:

> aptitude -s -R install libboost-dev

The binary package requires [this]("http://www.digitalfanatics.org/cal/socketw/"). Then you need to add the package to dpkg's database like [this]("http://ubuntuforums.org/showthread.php?t=2007861"). I ran into comparable issue's as well.

Keep trying!

---

### Post by louie123 on 2012-07-08
> **Rexilion said:**
> Your build probably fails because you don't have boost installed:



The binary package requires [this]("http://www.digitalfanatics.org/cal/socketw/"). Then you need to add the package to dpkg's database like [this]("http://ubuntuforums.org/showthread.php?t=2007861"). I ran into comparable issue's as well.

Keep trying! i get this error aptitude -s -R install libboost-dev 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 195 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Would download/install/remove packages.

---

### Post by louie123 on 2012-07-08
> **louie123 said:**
> i get this error aptitude -s -R install libboost-dev 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 195 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Would download/install/remove packages. i dont know how to install [SIZE=6]SocketW[/SIZE]

---

### Post by ubudog on 2012-07-08
> **louie123 said:**
> i dont know how to install [SIZE=6]SocketW[/SIZE]

Look at [this]("http://www.rigsofrods.com/wiki/pages/Compiling_3rd_party_libraries") page, and scroll down to MySocketW.

---

### Post by louie123 on 2012-07-08
> **ubudog said:**
> Look at [this]("http://www.rigsofrods.com/wiki/pages/Compiling_3rd_party_libraries") page, and scroll down to MySocketW. that help  but when i open up the deb i still get this error Dependency is not satisfiable: socketw (>= 0)  also when i try to install caelum i get boost not found i have diffent versions of boost installed. this is what the error looks like this a picture of my desktop with the error [http://i.imgur.com/1oerE.png](http://i.imgur.com/1oerE.png)[IMG]http://http://i.imgur.com/1oerE.png[/IMG]

---

### Post by mc4man on 2012-07-08
You really got yourself a bit of a mess here - sorta goes with your posting style

A few thoughts

First - you are running an eol version of ubuntu, have you switched your sources to the old-release repo so you can get any needed package(s) if not already installed?

2nd - you're mixing 2 paths - building 3rd party sources but then , (when & if completed properly), instead of also building the  Rigs of rods source trying to install a .deb that will require packaged versions of many of those 3rd party sources. 

Just will not work unless you then create & install dummy packages for all the required 3rd party sources you built (as Rexilion somewhat alluded to), and even then may not..


You're may be building some sources you may not need to - like
freeimage
ois
The 10.10 versions may be ok, you'd need the -dev packages if building ROR

Your best bet would be to build all the sources, one at a time & don't proceed until each is done right.
Then build the RoR source

If doing that I'd start over, first making sure all of these are installed
```
sudo apt-get install automake subversion cmake build-essential libfreetype6-dev libzzip-dev nvidia-cg-toolkit \
 libwxgtk2.8-dev libfreeimage-dev libgl1-mesa-dev libxrandr-dev libx11-dev libxt-dev libxaw7-dev \
 libglu1-mesa-dev libxxf86vm-dev libboost-dev pkg-config uuid-dev libuuid1 libgtk2.0-dev liblua5.1-0-dev \
 libopenal-dev scons cmake-qt-gui libboost-all-dev libcurl4-openssl-dev doxygen mercurial
```
as shown here - 
[http://www.rigsofrods.com/wiki/pages/Compiling_Sources_under_Linux](http://www.rigsofrods.com/wiki/pages/Compiling_Sources_under_Linux)

Then once done with all the 3rd party sources  build & install RoR itself

Otherwise the place where the .deb came from has all the 'required' packages avail. *may not be all the needed or desired

[http://apt.rigsofrods.com/dists/lucid/main/binary-amd64/](http://apt.rigsofrods.com/dists/lucid/main/binary-amd64/)

You'd download each of them & install one bu one starting with Ogre
There is a packaging issue between Ogre & pagedGeometry but that can be fixed with dpkg, install pagedGeometry last with 
sudo dpkg -i  --force overwrite /path/to/pagedGeometry-1.5-amd64.deb

Whether you'd need hydra don't know??

I'd make sure I had the old-release repo enabled, update sources, run the apt-get from above & build everything, 1 source at a time

---

### Post by louie123 on 2012-07-08
i installed all of those  when i open the deb i get the same error  i got a new version of wine 1.5.7 it runs ror perfectly

---

### Post by gandalf3 on 2012-07-16
how? i tried the same version (of wine), but when it installs directx fails to install.. :(
EDIT
i have attempted to compile it as well.. didn't work but somebody gave me they're successfully compiled build :)
[http://ubuntuforums.org/showthread.php?t=1962218&page=2](http://ubuntuforums.org/showthread.php?t=1962218&page=2)
but it still doesn't run on my machine..

---

### Post by gandalf3 on 2012-07-17
also where did you get the link for the .deb file?
is there one for intel 32 bit?
(my processor is 64 bits, but i didn't know until after i installed ubuntu :P)

---

### Post by louie123 on 2012-07-30
> **gandalf3 said:**
> how? i tried the same version (of wine), but when it installs directx fails to install.. :(
EDIT
i have attempted to compile it as well.. didn't work but somebody gave me they're successfully compiled build :)
[http://ubuntuforums.org/showthread.php?t=1962218&page=2](http://ubuntuforums.org/showthread.php?t=1962218&page=2)
but it still doesn't run on my machine..
use winetricks to install directx maybe that might help im using wine 1.5.7 in play on linux it runs better in 1.5.9 it fixs graphics bugs

---

### Post by louie123 on 2012-07-30
> **gandalf3 said:**
> also where did you get the link for the .deb file?
is there one for intel 32 bit?
(my processor is 64 bits, but i didn't know until after i installed ubuntu :P)
i dont   know if theres on for 32 bit but they have the 64 bit deb do you want the link

---

### Post by gandalf3 on 2012-07-30
really? that would be great! (im planing on upgrading to 12.04 64 bit since now i know what my CPU is :P)
it is for Intel chips, right?
thanks! :D

---

