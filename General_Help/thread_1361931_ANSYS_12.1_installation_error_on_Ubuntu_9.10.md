---
title: "ANSYS 12.1 installation error on Ubuntu 9.10"
date: 2009-12-22
forum: General Help
---

### Post by nzy102 on 2009-12-22
Hi:

I tried to install ANSYS 12.1 (using root) on my ubuntu 9.1 (64 bits) and got some errors shown below in red. Can anyone here know how to resolve it? Thanks a lot.

Ning

=========================================================

>>>--------------------------------------->
Start Installation: Tue Dec 22 11:32:37 AM PST 2009
Revision: 12.1
Platform specifics:
    Linux YANGN6-D1 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux
Username of Installer: root
Initial mount directory:
    /media/cdrom0
Installation Directory:
   /ansys_inc

Selected Platforms/Products:
  Linux x64:
    ANSYS, Inc. Products
        ANSYS Mechanical / Electromagnetics / Explicit Products
            ANSYS AUTODYN
            ANSYS LS-DYNA
        ANSYS CFD Products
            ANSYS CFD-Post
            ANSYS CFX
            ANSYS TurboGrid
            ANSYS FLUENT
    ANSYS Additional tools
        ANSYS ICEM CFD
            ANSYS ICEM CFD Pro/ENGINEER Interface
            ANSYS ICEM CFD Unigraphics NX Interface
        ANSYS Icepak
            Icepak
    ANSYS Geometry Interfaces
        Pro/ENGINEER
        Unigraphics NX
        Acis
        Parasolid
        Catia, Version 4
Reading the installation media contents - please wait.

  Extraction: /media/cdrom0/common/LINX64.GZ ...
  Extraction: /media/cdrom0/hlptool1/HLPTOOL1.TGZ ...
  Extraction: /media/cdrom0/hlpfiles/HLPFILES.TGZ ...
  Extraction: /media/cdrom0/hlpserv/HLPSERV.TGZ ...
  Extraction: /media/cdrom0/framewrk/LINX64.TGZ ...
  Extraction: /media/cdrom0/addins/LINX64.TGZ ...
  Extraction: /media/cdrom0/corewb/LINX64.GZ ...
  Extraction: /media/cdrom0/wbonebld/LINX64.TGZ ...
  Extraction: /media/cdrom0/engdata/LINX64.GZ ...
  Extraction: /media/cdrom0/rsm/RSM.TGZ ...
  Extraction: /media/cdrom0/icemwb/LINX64.TGZ ...
  Extraction: /media/cdrom0/mono/LINX64_1.TGZ ...
  Extraction: /media/cdrom0/mono/LINX64_2.TGZ ...
  Extraction: /media/cdrom0/mono/LINX64_3.TGZ ...
  Extraction: /media/cdrom0/addwb/LINX64.TGZ ...
  Extraction: /media/cdrom0/addinekm/LINX64.TGZ ...
  Extraction: /media/cdrom0/addekm/LINX64.TGZ ...
  Extraction: /media/cdrom0/ekm/LINX64.TGZ ...
  Extraction: /media/cdrom0/addts/LINX64.TGZ ...
  Extraction: /media/cdrom0/javajre/LINX64.TGZ ...
  Extraction: /media/cdrom0/ansys/LINX64.GZ ...
  Extraction: /media/cdrom0/addansys/LINX64.TGZ ...
  Extraction: /media/cdrom0/solver/LINX64.GZ ...
  Extraction: /media/cdrom0/data/DATA.GZ ...
  Extraction: /media/cdrom0/apdl/APDL.GZ ...
  Extraction: /media/cdrom0/geomacis/LINX64.GZ ...
  Extraction: /media/cdrom0/geompara/LINX64.GZ ...
  Extraction: /media/cdrom0/geomcat4/LINX64.GZ ...
  Extraction: /media/cdrom0/hpmpi/LINX64.GZ ...
  Extraction: /media/cdrom0/addmech/LINX64.TGZ ...
  Extraction: /media/cdrom0/autodyn/LINX64.GZ ...
  Extraction: /media/cdrom0/lsdyna/LINX64.GZ ...
  Extraction: /media/cdrom0/addpost/LINX64.TGZ ...
  Extraction: /media/cdrom0/cfx/linuxop/cfxpost.gz ...
  Extraction: /media/cdrom0/cfx/share/basic.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/perl580.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/othertls.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/shlib.gz ...
  Extraction: /media/cdrom0/cfx/share/gccsrc.gz ...
  Extraction: /media/cdrom0/cfx/share/mtsdc.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/launcher.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/gfort430.gz ...
  Extraction: /media/cdrom0/cfx/share/cuecom.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/qt443.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/qwt511.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/cuecom.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/cfxcpp.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/mesa71.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/psttls.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/mpegtls.gz ...
  Extraction: /media/cdrom0/cfx/share/mpegsrc.gz ...
  Extraction: /media/cdrom0/cfx/share/instpost.gz ...
  Extraction: /media/cdrom0/cfx/share/ccllib.gz ...
  Extraction: /media/cdrom0/cfx/share/hfpdfm.gz ...
  Extraction: /media/cdrom0/cfx/share/hfpdf.gz ...
  Extraction: /media/cdrom0/cfx/share/ohelp.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/java15.gz ...
  Extraction: /media/cdrom0/cfx/share/examples.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/areq.gz ...
  Extraction: /media/cdrom0/addcfx/LINX64.TGZ ...
  Extraction: /media/cdrom0/cfx/linuxop/cfxpre.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/import.gz ...
  Extraction: /media/cdrom0/cfx/share/cclmat.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/cfxrif.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/slvman.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/interp.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/export.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/slvbin.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/refiner.gz ...
  Extraction: /media/cdrom0/cfx/share/instcfx.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/pvm3.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/hpmpi.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/mpich.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/tgbin.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/tgtools.gz ...
  Extraction: /media/cdrom0/cfx/share/basic.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/perl580.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/othertls.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/shlib.gz ...
  Extraction: /media/cdrom0/cfx/share/gccsrc.gz ...
  Extraction: /media/cdrom0/cfx/share/mtsdc.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/launcher.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/gfort430.gz ...
  Extraction: /media/cdrom0/cfx/share/cuecom.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/qt443.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/qwt511.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/cuecom.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/cfxcpp.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/mesa71.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/psttls.gz ...
  Extraction: /media/cdrom0/cfx/share/tghelpm.gz ...
  Extraction: /media/cdrom0/cfx/share/tghelp.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/export.gz ...
  Extraction: /media/cdrom0/cfx/share/ohelp.gz ...
  Extraction: /media/cdrom0/cfx/linuxop/java15.gz ...
  Extraction: /media/cdrom0/cfx/share/tgexamp.gz ...
  Extraction: /media/cdrom0/cfx/share/insttbg.gz ...
  Extraction: /media/cdrom0/fluent/LINX64.TGZ ...
  Extraction: /media/cdrom0/addflunt/LINX64.TGZ ...
  Extraction: /media/cdrom0/icemcfd/LINX64.TGZ ...
  Extraction: /media/cdrom0/cart3d/LINX64.TGZ ...
  Extraction: /media/cdrom0/geomproe/LNX64_IC.TGZ ...
  Extraction: /media/cdrom0/geomug/LNX64_IC.TGZ ...
  Extraction: /media/cdrom0/hlpunxic/HLPUNXIC.TGZ ...
  Extraction: /media/cdrom0/icemtuto/ICEMTUTO.TGZ ...
  Extraction: /media/cdrom0/hlptool2/HLPTOOL2.TGZ ...
  Extraction: /media/cdrom0/icepak/LINX64.TGZ ...
  Extraction: /media/cdrom0/addicepk/LINX64.TGZ ...
  Extraction: /media/cdrom0/geomproe/LINX64.GZ ...
  Extraction: /media/cdrom0/geomunig/LINX64.GZ ...
  Extraction: /media/cdrom0/licserv/LINX64.TGZ ...
  Extraction: /media/cdrom0/license/LINX64.TGZ ...
  Extraction: /media/cdrom0/hlplic/HLPLIC.TGZ ...

Successfully copied .ans_uninstall.sh
Successfully copied xansuninstall.tcl

[COLOR=Red]Configuring WB Simulation script files ...
[%wc] Registry Editor
Information in /ansys_inc/v121/aisol/workbench.reg has been successfully entered into the registry.
ansyswbu.exe is not required ...
RegSvr32: LoadLibrary("/ansys_inc/v121/aisol/dll/linx64/libans.common.clrhostmonou.so") failed.
GetLastError returns 0x0000007e.
 ERROR: /ansys_inc/v121/aisol/workbench  -cmd /ansys_inc/v121/aisol/mw/bin-amd64_linux_optimized/regsvr32 -c -nodisplay /ansys_inc/v121/aisol/dll/linx64/libans.common.clrhostmonou.so failed 
RegSvr32: LoadLibrary("/ansys_inc/v121/aisol/dll/linx64/libans.common.controlsu.so") failed.
GetLastError returns 0x0000007e.
 ERROR: /ansys_inc/v121/aisol/workbench  -cmd /ansys_inc/v121/aisol/mw/bin-amd64_linux_optimized/regsvr32 -c -nodisplay /ansys_inc/v121/aisol/dll/linx64/libans.common.controlsu.so failed 
RegSvr32: LoadLibrary("/ansys_inc/v121/aisol/dll/linx64/libans.graphics.controlsu.so") failed.
GetLastError returns 0x0000007e.
 ERROR: /ansys_inc/v121/aisol/workbench  -cmd /ansys_inc/v121/aisol/mw/bin-amd64_linux_optimized/regsvr32 -c -nodisplay /ansys_inc/v121/aisol/dll/linx64/libans.graphics.controlsu.so failed 
RegSvr32: LoadLibrary("/ansys_inc/v121/aisol/dll/linx64/libans.graphics.graphutilityu.so") failed.
GetLastError returns 0x0000007e.
 ERROR: /ansys_inc/v121/aisol/workbench  -cmd /ansys_inc/v121/aisol/mw/bin-amd64_linux_optimized/regsvr32 -c -nodisplay /ansys_inc/v121/aisol/dll/linx64/libans.graphics.graphutilityu.so failed 
RegSvr32: LoadLibrary("/ansys_inc/v121/aisol/dll/linx64/libagpsutilcom.so") failed.
GetLastError returns 0x0000007e.
 ERROR: /ansys_inc/v121/aisol/workbench  -cmd /ansys_inc/v121/aisol/mw/bin-amd64_linux_optimized/regsvr32 -c -nodisplay /ansys_inc/v121/aisol/dll/linx64/libagpsutilcom.so failed 
RegSvr32: LoadLibrary("/ansys_inc/v121/aisol/dll/linx64/libans.cadint.xmlexportcom.so") failed.
GetLastError returns 0x0000007e.
 ERROR: /ansys_inc/v121/aisol/workbench  -cmd /ansys_inc/v121/aisol/mw/bin-amd64_linux_optimized/regsvr32 -c -nodisplay /ansys_inc/v121/aisol/dll/linx64/libans.cadint.xmlexportcom.so failed 
RegSvr32: LoadLibrary("/ansys_inc/v121/aisol/dll/linx64/libans.cadint.xmlimportcom.so") failed.
GetLastError returns 0x0000007e.
 ERROR: /ansys_inc/v121/aisol/workbench  -cmd /ansys_inc/v121/aisol/mw/bin-amd64_linux_optimized/regsvr32 -c -nodisplay /ansys_inc/v121/aisol/dll/linx64/libans.cadint.xmlimportcom.so failed 
RegSvr32: LoadLibrary("/ansys_inc/v121/aisol/dll/linx64/libans.cadint.configmgrcom.so") failed.
GetLastError returns 0x0000007e.
 ERROR: /ansys_inc/v121/aisol/workbench  -cmd /ansys_inc/v121/aisol/mw/bin-amd64_linux_optimized/regsvr32 -c -nodisplay /ansys_inc/v121/aisol/dll/linx64/libans.cadint.configmgrcom.so failed 
RegSvr32: LoadLibrary("/ansys_inc/v121/aisol/dll/linx64/libans.cadint.pluginfemcom.so") failed.
GetLastError returns 0x0000007e.
 ERROR: /ansys_inc/v121/aisol/workbench  -cmd /ansys_inc/v121/aisol/mw/bin-amd64_linux_optimized/regsvr32 -c -nodisplay /ansys_inc/v121/aisol/dll/linx64/libans.cadint.pluginfemcom.so failed 
RegSvr32: LoadLibrary("/ansys_inc/v121/aisol/dll/linx64/libans.cadint.pmexportercom.so") failed.
GetLastError returns 0x0000007e.
 ERROR: /ansys_inc/v121/aisol/workbench  -cmd /ansys_inc/v121/aisol/mw/bin-amd64_linux_optimized/regsvr32 -c -nodisplay /ansys_inc/v121/aisol/dll/linx64/libans.cadint.pmexportercom.so failed 
RegSvr32: LoadLibrary("/ansys_inc/v121/aisol/dll/linx64/libfepsexportcom.so") failed.
GetLastError returns 0x0000007e.
 ERROR: /ansys_inc/v121/aisol/workbench  -cmd /ansys_inc/v121/aisol/mw/bin-amd64_linux_optimized/regsvr32 -c -nodisplay /ansys_inc/v121/aisol/dll/linx64/libfepsexportcom.so failed 
RegSvr32: LoadLibrary("/ansys_inc/v121/aisol/dll/linx64/libagpsenginecom.so") failed.
GetLastError returns 0x0000007e.
 ERROR: /ansys_inc/v121/aisol/workbench  -cmd /ansys_inc/v121/aisol/mw/bin-amd64_linux_optimized/regsvr32 -c -nodisplay /ansys_inc/v121/aisol/dll/linx64/libagpsenginecom.so failed 
Input arguments are 
Executing /ansys_inc/v121/Tools/mono/Linux64/bin/mono /ansys_inc/v121/commonfiles/CAD/bin/linx64/Ans.CadInt.CADConfigurationUtility.exe 
NX   ICEM CFD ..... Not Configured[/COLOR]


Configuring ANSYS script files ...
Setting File Permissions for ANSYS ...
Configuring ANSYS CFD Post ...
Configuring ANSYS CFX ...
Setting up a default parallel host configuration
Configuring ANSYS TurboGrid ...
Configuring Geometry Interface for Pro/ENGINEER script files ...
Setting File Permissions for Geometry Interface for Pro/ENGINEER files ...
Setting File Permissions for Unigraphics NX Geometry Interface files ...
Configuring Licensing script files ...


 ***** IMPORTANT NOTE: ERRORS were detected! *****
 ***** Log File: /ansys_inc/install.err *****

Installation Complete: Tue Dec 22 11:44:36 AM PST 2009
<---------------------------------------<<<

=========================================================

---

### Post by stevendiehl on 2010-01-27
I am getting the exact same error message on my 64bit Ubuntu. Did you ever get Ansys to run? I am having trouble starting workbench and the design modeler. If you check the error log in the install directory, there are just 3 more messages that might be related to the problem, for some reason, they are not shown in the gui report...

/localsoft/ansys_inc/v121/aisol/CommonFiles/linx64/activepimgru.exe: error while loading shared libraries: libComponentSystem.so: cannot open shared object file: No such file or directory
/localsoft/ansys_inc/v121/aisol/CommonFiles/linx64/readerhostu.exe: error while loading shared libraries: libComponentSystem.so: cannot open shared object file: No such file or directory
/localsoft/ansys_inc/v121/aisol/CommonFiles/linx64/wbscriptu.exe: error while loading shared libraries: libComponentSystem.so: cannot open shared object file: No such file or directory

Does anyone have a clue as to what is going on? Changing from Ubuntu to Redhat or SUSE would be a really big hassle right now. 

Thanks, 
Steven

---

### Post by fennec101 on 2010-02-04
Hello all,
DId you guys resolve the problem?

---

### Post by stevendiehl on 2010-02-08
No luck yet from my side, anyone else? I will try and contact customer support this week and see if they can be helpful, but my guess they will just say that my linux distro is not supported and that's gonna be it...
 
Steven

---

### Post by vladeta on 2010-02-15
+1
Same here with 8.04 hardy.
Has someone received some answer from customer support other than, change your linux distro. tnx

---

### Post by jsmanian on 2010-02-17
Hi


   This [COLOR=Red]**[link]("http://www.cfd-online.com/Forums/cfx/25236-ansys-workbench-uncertified-linux-distros.html")**[/COLOR] may be useful to install Ansys 12.1 in Ubuntu 9.10. Just try this:p

Give the feedback please.

---

### Post by stevendiehl on 2010-03-18
[SIZE=2]Hey all, [/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I just got this message about a linux patch from ANSYS, which may be related to our problems:[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]"ANSYS, Inc. is pleased to announce that ANSYS 12.1 has been updated with additional Linux platform support. The software is now available for download via the [/SIZE][[SIZE=2]ANSYS Customer Portal[/SIZE]]("http://ansys-list-5.c.topica.com/maanRtuabWPZ2bOtEUIeafpKZv/")[SIZE=2].

The key features debuting in this update are completed Linux ports of ANSYS Mechanical, ANSYS POLYFLOW, and ANSYS Engineering Knowledge Manager (EKM) Desktop. **In addition, improvements have been made to the robustness of the Linux versions of ANSYS Workbench, ANSYS DesignModeler, ANSYS Meshing, and FE Modeler**."[/SIZE]

Did anyone try this yet? I don't have the time right at this moment to try...
 
Steven

---

### Post by elbasharat on 2010-06-23
can anyone give me ANsys customer portal ID and password please

---

### Post by donminoti on 2010-11-20
Hi every bady,

sorry ,i know that i'm late. i have the same  problem (same error message as the one posted by nzy102) with ANSYS 12   on ubuntu 10.10. have you found any solution? , i m new on Linux! 

thanks.

---

### Post by sazawal on 2011-02-24
Hi everyone,

I installed ansys 12.1 on my 64 bit Ubuntu 10.10. I guess the installation was successful but I am not able to run the software. Can anyone help me out with it. I am posting my terminal output when I tried to run the ansys script

```
$/opt/ansys_inc/v121/ansys/bin#./ansys121

*** IMPORTANT LICENSING MESSAGE ***

ANSYS LICENSE MANAGER ERROR:
No servers provided.
       ANSYSLI_SERVERS:  
       FLEXlm Servers: 1055@microsoft

 *** ERROR - ANSYS license not available.

 DATA INPUT WRITTEN ON /opt/ansys_inc/shared_files/licensing/lic_admin/file.log                                                                                                                                                                                                            

+--------------------- A N S Y S   S T A T I S T I C S ------------------------+

Release: 12.1BETA   UP20090528   Version: LINUX x64   
Date Run: 02/23/2011   Time: 22:19

Number of cores:   0 (Shared Memory Parallel)

Job Name: file
Working Directory: 

Elapsed time spent pre-processing model (/PREP7)  :      0.0 seconds
Elapsed time spent solution - preprocessing       :      0.0 seconds
Elapsed time spent computing solution             :      0.0 seconds
Elapsed time spent solution - postprocessing      :      0.0 seconds
Elapsed time spent post-processing model (/POST1) :      0.0 seconds

+------------------ E N D   A N S Y S   S T A T I S T I C S -------------------+


 *---------------------------------------------------------------------------*
 |                                                                           |
 |                            ANSYS RUN COMPLETED                            |
 |                                                                           |
 |---------------------------------------------------------------------------|
 |                                                                           |
 |            Release 12.1BETA       UP20090528         LINUX x64            |
 |                                                                           |
 |---------------------------------------------------------------------------|
 |                                                                           |
 |   Maximum Scratch Memory Used       =           0 Words        0.000 MB   |
 |                                                                           |
 |---------------------------------------------------------------------------|
 |                                                                           |
 |        CP Time      (sec) =          0.570       Time  =  22:19:06        |
 |        Elapsed Time (sec) =          1.000       Date  =  02/23/2011      |
 |                                                                           |
 *---------------------------------------------------------------------------*
```I dont know if the problem is due to license or due to servers(ANSYSLI_SERVERS, FLEXlm Servers). I have never worked on ansys before, perhaps you people can help me out where I am stuck. Thanks in advance

---

### Post by gianluca.pettinello on 2012-05-13
Hi all,
I post here my experience with Ansys 14 and ubuntu 12.04 hoping it can be of help.

After installing, with lsb package installed you have to start correctly the license manager. In my case flexlm was not starting, so I had to build a script wrapping the startup of ansys where I manually started lmgrd. Then Design modeler was not working so I had to download the following packages from oneiric and extract the libraries (not install!) in /yourinstallationpath/v140/commonfiles/MainWin/linx64/mw/lib-amd64_linux_optimized

libxext6
libxrender1
libxfixes3
 
Here is the final wrapping script:
#!/bin/sh
case "$1" in
    'start')
        LM_RUN=`ps -e | grep lmgrd`
        AS_RUN=`ps -e | grep ansysli_server`
        if [ "$LM_RUN" = "" ]; then
            /yourinstallationpath/shared_files/licensing/linx64/lmgrd -c /yourinstallationpath/shared_files/licensing/license.dat #choose the path where your license.dat stays
        fi
        if [ "$AS_RUN" = "" ]; then
            /yourinstallationpath/shared_files/licensing/start_ansysli
        fi
        ;; 
    'stop')
        /yourinstallationpath/shared_files/licensing/stop_ansysli    
        ;;
    *)
        LM_RUN=`ps -e | grep lmgrd`
        AS_RUN=`ps -e | grep ansysli_server`
        if [ "$LM_RUN" = "" ]; then
            /yourinstallationpath/licensing/linx64/lmgrd -c /yourinstallationpath/shared_files/licensing/license.dat
        fi
        if [ "$AS_RUN" = "" ]; then
            /yourinstallationpath/licensing/start_ansysli
        fi
        LD_LIBRARY_PATH=/yourinstallationpath/v140/commonfiles/MainWin/linx64/mw/lib-amd64_linux_optimized:$LD_LIBRARY_PATH
        export LD_LIBRARY_PATH
        uname26 /yourinstallationpath/v140/Framework/bin/Linux64/runwb2
        ;;
esac

Lost one week of my life for this problem!
Bye

---

### Post by okidanokh on 2012-09-20
Hi guys,

I followed all the instruction on this thread (copying the libs form oneiric) and also from cfdonline, but nothing.

I was able to run cfx and icemcfd and the licence manager without any problem.

I have the same issue launching form WB the Geometry Modeler and Mesher.
I m using ansys 14 on ubuntu 12.04.

Please let me know a robust procedure to run the geometry modeler.

Thanks a lot!

---

### Post by gianluca.pettinello on 2013-03-30
Hi all,
I come back after a long time with some other tips.
I switched to Arch Linux because I wanted a rolling release and was not afraid of extra configuration and tweaking.
So beautiful distro, by the way I installed Unity because I find it awesome..
But no clue how to install ANSYS 14... better I was able to install it but the design modeler was not starting.
So after other 4 days of hacking, and no help from internet, I was able to get everything working.
Compared to the previous post for Ubuntu there are some extra tweaking:
1) create the script /usr/bin/arch which simply echoes your architecture:
#! /bin/bash
uname -m

2) create the script /usr/bin/rpm which echoes your glibc version
#!/bin/bash
echo glibc-2.17

3) start the installation script with the following command, which fakes the installer thinking there is a 2.6.x kernel
setarch x86_64 --uname-2.6 /path/to/installer

3) Install in the usual position, /opt/ansys/v140/commonfiles/MainWin/linx64/mw/lib-amd64_linux_optimized, the missing old libraries
/opt/ansys/v140/commonfiles/MainWin/linx64/mw/lib-amd64_linux_optimized/libXext.so.6
/opt/ansys/v140/commonfiles/MainWin/linx64/mw/lib-amd64_linux_optimized/libXext.so.6.4.0
/opt/ansys/v140/commonfiles/MainWin/linx64/mw/lib-amd64_linux_optimized/libXfixes.so.3
/opt/ansys/v140/commonfiles/MainWin/linx64/mw/lib-amd64_linux_optimized/libXfixes.so.3.1.0
/opt/ansys/v140/commonfiles/MainWin/linx64/mw/lib-amd64_linux_optimized/libXrender.so.1
/opt/ansys/v140/commonfiles/MainWin/linx64/mw/lib-amd64_linux_optimized/libXrender.so.1.3.0
You can take the oneiric packages

4) create the script /usr/bin/ansys
#!/bin/sh
case "$1" in
    'start')
        LM_RUN=`ps -e | grep lmgrd`
        AS_RUN=`ps -e | grep ansysli_server`
        if [ "$LM_RUN" = "" ]; then
            /opt/ansys/shared_files/licensing/linx64/lmgrd -c /opt/ansys/shared_files/licensing/license.dat
        fi
        if [ "$AS_RUN" = "" ]; then
            /opt/ansys/shared_files/licensing/start_ansysli
        fi
        ;; 
    'stop')
        /opt/ansys/shared_files/licensing/stop_ansysli    
        ;;
    *)
        LM_RUN=`ps -e | grep lmgrd`
        AS_RUN=`ps -e | grep ansysli_server`
        if [ "$LM_RUN" = "" ]; then
            /opt/ansys/shared_files/licensing/linx64/lmgrd -c /opt/ansys/shared_files/licensing/license.dat
        fi
        if [ "$AS_RUN" = "" ]; then
            /opt/ansys/shared_files/licensing/start_ansysli
        fi
        #Necessary for Ubuntu
        LD_LIBRARY_PATH=/opt/ansys/v140/commonfiles/MainWin/linx64/mw/lib-amd64_linux_optimized:$LD_LIBRARY_PATH
        export LD_LIBRARY_PATH
        setarch x86_64 --uname-2.6 /opt/ansys/v140/Framework/bin/Linux64/runwb2
        ;;
esac
That's all. It worked for me.
Hope it is useful also for the others

Be free Use your mind
Gianluca

---

### Post by Badal_Yadav on 2013-09-20
Hi there. 

I really really need your help. 

I am not a new user to ubuntu, but all I have been doing is running matlab and C++ code. 
My intentions are to install ANSYS on Ubuntu12.04 on one of the computers in my lab.  
I followed your instructions on the above posts, but it didn't quite work for me. 

Here is what I did: 

1. Installed Ubuntu 12.04LTS on the system. 
2. Ran an update & installed 'lsb' package. 
3. Downloaded & Installed ICEMCFD1457_LINX64. I was promted with installation of license manager which I installed too. 

What I expected after doing this was to be able to run the file "/home/siva/ansys_inc/v145/icemcfd/linux64_amd/bin/icemcfd"
When I tried to run it, nothing happened. The computer remained silent as if it wasn't supposed to do anything.

4. Then I downloaded the files "libxfixes3_5.0-4ubuntu1newyork1_amd64.deb", "libxrender1_0.9.6-2_amd64.deb", "libxext6_1.3.0-3_amd64.deb". 
Extracted them and copied the files "libXfixes.so.3.1.0", "libXrender.so.1.3.0" & "libXext.so.6.4.0" to the location: 
"/home/siva/ansys_inc/v145/commonfiles/MainWin/linx64/mw/lib-amd64_linux_optimized". 

5. I carefully ran your script and got the following results: 

$ #!/bin/sh
$ case "$1" in
> 'start')
> LM_RUN=`ps -e | grep lmgrd`
> AS_RUN=`ps -e | grep ansysli_server`
> if [ "$LM_RUN" = "" ]; then
> /home/siva/ansys_inc/shared_files/licensing/linx64/lmgrd -c /home/siva/ansys_inc/shared_files/licensing/license.dat
> fi
> if [ "$AS_RUN" = "" ]; then
> /home/siva/ansys_inc/shared_files/licensing/start_ansysli 
> fi
> ;;
> 'stop')
> /home/siva/ansys_inc/shared_files/licensing/stop_ansysli 
> ;;
> *)
> LM_RUN=`ps -e | grep lmgrd`
> AS_RUN=`ps -e | grep ansysli_server`
> if [ "$LM_RUN" = "" ]; then
> /home/siva/ansys_inc/shared_files/licensing/linx64/lmgrd -c /home/siva/ansys_inc/shared_files/licensing/license.dat
> fi
> if [ "$AS_RUN" = "" ]; then
> /home/siva/ansys_inc/shared_files/licensing/start_ansysli 
> fi
> LD_LIBRARY_PATH=/home/siva/ansys_inc/v145/commonfiles/MainWin/linx64/mw/lib-amd64_linux_optimized:$LD_LIBRARY_PATH
> uname26 /home/siva/ansys_inc/v145/Framework/bin/Linux64/runwb2 
> ;;
> esac
16:04:58 (lmgrd) -----------------------------------------------
16:04:58 (lmgrd)   Please Note:
16:04:58 (lmgrd) 
16:04:58 (lmgrd)   This log is intended for debug purposes only.
16:04:58 (lmgrd)   In order to capture accurate license
16:04:58 (lmgrd)   usage data into an organized repository,
16:04:58 (lmgrd)   please enable report logging. Use Flexera Software, Inc.'s
16:04:58 (lmgrd)   software license administration  solution,
16:04:58 (lmgrd)   FLEXnet Manager, to  readily gain visibility
16:04:58 (lmgrd)   into license usage data and to create
16:04:58 (lmgrd)   insightful reports on critical information like
16:04:58 (lmgrd)   license availability and usage. FLEXnet Manager
16:04:58 (lmgrd)   can be fully automated to run these reports on
16:04:58 (lmgrd)   schedule and can be used to track license
16:04:58 (lmgrd)   servers and usage across a heterogeneous
16:04:58 (lmgrd)   network of servers including Windows NT, Linux
16:04:58 (lmgrd)   and UNIX. Contact Flexera Software, Inc. at
16:04:58 (lmgrd)   [www.flexerasoftware.com](www.flexerasoftware.com) for more details on how to
16:04:58 (lmgrd)   obtain an evaluation copy of FLEXnet Manager
16:04:58 (lmgrd)   for your enterprise.
16:04:58 (lmgrd) 
16:04:58 (lmgrd) -----------------------------------------------
16:04:58 (lmgrd) 
16:04:58 (lmgrd) 
16:04:58 (lmgrd) Can't make directory /usr/tmp/.flexlm, errno: 2(No such file or directory)
16:04:58 (lmgrd) license manager: can't initialize:Cannot find license file.
16:04:58 (lmgrd) The license files (or license server system network addresses) attempted are
16:04:58 (lmgrd) listed below.  Use LM_LICENSE_FILE to use a different license file,
16:04:58 (lmgrd) or contact your software provider for a license file.
16:04:58 (lmgrd) Filename: "/usr/local/flexlm/licenses/license.dat"
16:04:58 (lmgrd) License Path: "/usr/local/flexlm/licenses/license.dat"
16:04:58 (lmgrd) FLEXnet Licensing error:-1,359
16:04:58 (lmgrd) System Error:2 No such file or directory
16:04:58 (lmgrd) For further information, refer to the FLEXnet Licensing documentation,available at "www.flexerasoftware.com".
16:04:58 (lmgrd) Using license file "/usr/local/flexlm/licenses/license.dat"
uname26: command not found

_____________________________

I am still unable to run icemcfd. 

I will be grateful to you if you can help me in doing this. 
Firstly, I really want to be able to launch the 'icemcfd' file.

Many thanks.

---

