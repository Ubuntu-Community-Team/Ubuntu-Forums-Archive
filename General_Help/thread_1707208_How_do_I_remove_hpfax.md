---
title: "How do I remove hpfax??"
date: 2011-03-15
forum: General Help
---

### Post by jerremy-tamlin on 2011-03-15
I often get a crash report telling me that "hpfax" has closed unexpectedly.
Whenever I do almost anything with my printer setup it crashes.

Steps to replicate:
  System->Administration->Printing
  Click "Add" to add a printer

These crashes didn't seem too important before because everything kept working but now neither my HP-Deskjet-3050 or my HP-Photosmart-C4400 can be detected as a scanner by SANE!!

The symptoms are the same as those described here [http://ubuntuforums.org/showthread.php?t=578879](http://ubuntuforums.org/showthread.php?t=578879)

This thread here [http://ubuntuforums.org/showthread.php?t=329452](http://ubuntuforums.org/showthread.php?t=329452) suggests that the error is connected to hplip which "hpfax" is supposed to be a part of.

```
HPLIP is composed of: 
 * System services to handle communications with the printers 
 * HP CUPS backend driver (hp:) with bi-directional communication with HP printers (provides printer status feedback to CUPS and enhanced HPIJS
   functionality such as 4-side full-bleed printing support) 
 * HP CUPS backend driver for sending faxes **(hpfax:)** 

```

Since hpfax is crashing I thought this must be the problem and so I removed hplip.

```
sudo aptitude purge hplip
```

But even after restarting I still get the crash reports for hpfax even though hplip is not installed!!??

```
sudo aptitude show hplip
Package: hplip
State: not installed
Version: 3.10.2-2ubuntu2.2

```
```
sudo aptitude search hplip
p   hplip                                                                 - HP Linux Printing and Imaging System (HPLIP)                                    
p   hplip-cups                                                            - HP Linux Printing and Imaging - CUPS Raster driver (hpcups)                     
p   hplip-data                                                            - HP Linux Printing and Imaging - data files                                      
p   hplip-dbg                                                             - HP Linux Printing and Imaging - debugging information                           
p   hplip-doc                                                             - HP Linux Printing and Imaging - documentation                                   
p   hplip-gui                                                             - HP Linux Printing and Imaging - GUI utilities                                   
v   hplip-ppds           
```

Can anyone help me to remove this hpfax!!?? I don't send faxes and I really need my scanners back! They were working fine before hpfax started crashing.

---

### Post by jerremy-tamlin on 2011-04-05
Bummer :(
I hate having problems no one can help with :(

---

