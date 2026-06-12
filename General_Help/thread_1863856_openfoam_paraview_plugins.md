---
title: "openfoam paraview plugins"
date: 2011-10-18
forum: General Help
---

### Post by ilene2011 on 2011-10-18
after the installation of openfoam and when i m making paraview to install paraview plugins i found errors like 
:

Could NOT find Qt4: Found unsuitable version "4.3.4", but required is at least "4.6.0" (found /usr/bin/qmake-qt4)
-- Plugin: Reader/Writer for Analyze and NIfTI. enabled
-- Could NOT find Qt4: Found unsuitable version "4.3.4", but required is at least "4.6.0" (found /usr/bin/qmake-qt4)
-- Plugin: Override time requests disabled
-- Could NOT find Qt4: Found unsuitable version "4.3.4", but required is at least "4.6.0" (found /usr/bin/qmake-qt4)
CMake Error at CMakeLists.txt:345 (EXPORT):
  export given target "QtTesting" which is not built by this project.


-- Configuring development install...
-- Configuring incomplete, errors occurred!
    Starting make
make: *** Pas de cibles spécifiées et aucun makefile n'a été trouvé. Arrêt.
Command exited with non-zero status 2
0.00user 0.00system 0:00.08elapsed 4%CPU (0avgtext+0avgdata 0maxresident)k
400inputs+0outputs (3major+302minor)pagefaults 0swaps
    Done make
    Installing ParaView to /home/bahloul/OpenFOAM/ThirdParty-2.0.1/platforms/linuxGcc/paraview-3.10.1
make: *** Pas de règle pour fabriquer la cible « install ». Arrêt.
    ---
    Installation complete for paraview-3.10.1
    Set environment variables:

        export ParaView_DIR=/home/bahloul/OpenFOAM/ThirdParty-2.0.1/platforms/linuxGcc/paraview-3.10.1
        export PATH=$ParaView_DIR/bin:$PATH
        export PV_PLUGIN_PATH=$FOAM_LIBBIN/paraview-3.10
    ---
 plz help how to proceed?

---

### Post by howefield on 2011-10-18
Thread to the "*General Help*" forum.

---

