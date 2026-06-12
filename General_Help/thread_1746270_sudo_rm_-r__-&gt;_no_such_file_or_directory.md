---
title: "sudo rm -r * -&gt; no such file or directory"
date: 2011-05-01
forum: General Help
---

### Post by Abisso on 2011-05-01
Ok, I have a mounted external hard drive with just one partition and a NTFS filesystem, on Kubuntu 10.10. On that volume, I've got a folder which looks empty in Dolphin (even if I check "Show Hidden Files") and instead seems to have files if I type "dir" on a terminal.

The strangest thing is that both the recursive rm -rf and rm -r * fail to delete the folder and its contents.

```
gabriele@gabriele-System-Product-Name:/media/EXTERNAL$ sudo rm -rf coppa/
[sudo] password for gabriele:
rm: cannot remove `coppa/Progetti Cubase/piano2/Audio': Directory not empty
rm: cannot remove `coppa/Progetti Cubase/piano2/Images/Audio 11_20.peak': Is a directory
rm: cannot remove `coppa/Progetti Cubase/Ruggine/piano2/Audio': Directory not empty

```

```
root@gabriele-System-Product-Name:/media/EXTERNAL/coppa/Progetti Cubase/piano2/Images# sudo rm -r *
rm: cannot remove `Audio 11_20.peak': No such file or directory
rm: cannot remove `Audio 13_29.peak': No such file or directory
rm: cannot remove `Audio 13_30.peak': No such file or directory
rm: cannot remove `Audio 13_31.peak': No such file or directory
rm: cannot remove `Audio 13_32.peak': No such file or directory
rm: cannot remove `Audio 13_33.peak': No such file or directory
rm: cannot remove `Audio 13_34.peak': No such file or directory
rm: cannot remove `Audio 13_35.peak': No such file or directory
rm: cannot remove `Audio 13_36.peak': No such file or directory
rm: cannot remove `Audio 13_37.peak': No such file or directory
rm: cannot remove `Audio 13_38.peak': No such file or directory
rm: cannot remove `Audio 13_39.peak': No such file or directory
rm: cannot remove `Audio 14_00.peak': No such file or directory
rm: cannot remove `Audio 14_01.peak': No such file or directory
rm: cannot remove `Audio 14_02.peak': No such file or directory
rm: cannot remove `Audio 14_03.peak': No such file or directory
rm: cannot remove `Audio 14_04.peak': No such file or directory
rm: cannot remove `Audio 14_05.peak': No such file or directory
rm: cannot remove `Audio 14_07.peak': No such file or directory
rm: cannot remove `Audio 14_08.peak': No such file or directory
rm: cannot remove `Audio 14_09.peak': No such file or directory
rm: cannot remove `Audio 14_10.peak': No such file or directory
rm: cannot remove `Audio 14_11.peak': No such file or directory
rm: cannot remove `Audio 14_12.peak': No such file or directory
rm: cannot remove `Audio 14_13.peak': No such file or directory
rm: cannot remove `Audio 14_14.peak': No such file or directory
rm: cannot remove `Audio 14_15.peak': No such file or directory
rm: cannot remove `Audio 15_00.peak': No such file or directory
rm: cannot remove `Audio 15_01.peak': No such file or directory
rm: cannot remove `Audio 15_02.peak': No such file or directory
rm: cannot remove `Audio 15_03.peak': No such file or directory
rm: cannot remove `Audio 15_04.peak': No such file or directory
rm: cannot remove `Audio 15_05.peak': No such file or directory
rm: cannot remove `Audio 15_06.peak': No such file or directory
rm: cannot remove `Audio 15_08.peak': No such file or directory
rm: cannot remove `Audio 15_09.peak': No such file or directory
rm: cannot remove `Audio 15_10.peak': No such file or directory
rm: cannot remove `Audio 15_11.peak': No such file or directory
rm: cannot remove `Audio 15_12.peak': No such file or directory
rm: cannot remove `Audio 15_13.peak': No such file or directory
rm: cannot remove `Audio 15_14.peak': No such file or directory
rm: cannot remove `Audio 15_15.peak': No such file or directory
rm: cannot remove `Audio 15_16.peak': No such file or directory
rm: cannot remove `Audio 15_17.peak': No such file or directory
rm: cannot remove `Audio 15_18.peak': No such file or directory
rm: cannot remove `Audio 15_19.peak': No such file or directory
rm: cannot remove `Audio 15_20.peak': No such file or directory
rm: cannot remove `Audio 15_21.peak': No such file or directory
rm: cannot remove `Audio 15_22.peak': No such file or directory
rm: cannot remove `Audio 15_23.peak': No such file or directory
rm: cannot remove `Audio 16_01.peak': No such file or directory
rm: cannot remove `Audio 16_02.peak': No such file or directory
rm: cannot remove `Audio 16_03.peak': No such file or directory
rm: cannot remove `Audio 16_04.peak': No such file or directory
rm: cannot remove `Audio 16_05.peak': No such file or directory
rm: cannot remove `Audio 16_06.peak': No such file or directory
rm: cannot remove `Audio 16_07.peak': No such file or directory
rm: cannot remove `Audio 16_08.peak': No such file or directory
rm: cannot remove `Audio 16_09.peak': No such file or directory
rm: cannot remove `Audio 16_10.peak': No such file or directory
rm: cannot remove `Audio 16_11.peak': No such file or directory
rm: cannot remove `Audio 16_12.peak': No such file or directory
rm: cannot remove `Audio 16_13.peak': No such file or directory
rm: cannot remove `Audio 16_14.peak': No such file or directory
rm: cannot remove `Audio 16_15.peak': No such file or directory
rm: cannot remove `Audio 16_16.peak': No such file or directory
rm: cannot remove `Audio 16_18.peak': No such file or directory
rm: cannot remove `Audio 16_19.peak': No such file or directory
rm: cannot remove `Audio 16_20.peak': No such file or directory
rm: cannot remove `Audio 17_00.peak': No such file or directory
rm: cannot remove `Audio 17_01.peak': No such file or directory
rm: cannot remove `Audio 17_02.peak': No such file or directory
rm: cannot remove `Audio 17_03.peak': No such file or directory
rm: cannot remove `Audio 17_04.peak': No such file or directory
rm: cannot remove `Audio 17_05.peak': No such file or directory
rm: cannot remove `Audio 18_00.peak': No such file or directory
rm: cannot remove `Audio 18_01.peak': No such file or directory
rm: cannot remove `Audio 18_02.peak': No such file or directory
rm: cannot remove `Audio 18_03.peak': No such file or directory
rm: cannot remove `Audio 18_04.peak': No such file or directory
rm: cannot remove `Audio 18_05.peak': No such file or directory
rm: cannot remove `Audio 18_06.peak': No such file or directory
rm: cannot remove `Audio 18_08.peak': No such file or directory
rm: cannot remove `Audio 18_09.peak': No such file or directory
rm: cannot remove `Audio 18_10.peak': No such file or directory
rm: cannot remove `Audio 18_11.peak': No such file or directory
rm: cannot remove `Audio 18_12.peak': No such file or directory
rm: cannot remove `Audio 18_13.peak': No such file or directory
rm: cannot remove `Audio 18_14.peak': No such file or directory
rm: cannot remove `Audio 18_15.peak': No such file or directory
rm: cannot remove `Audio 18_16.peak': No such file or directory
rm: cannot remove `Audio 18_17.peak': No such file or directory
rm: cannot remove `Audio 18_18.peak': No such file or directory
rm: cannot remove `Audio 18_19.peak': No such file or directory
rm: cannot remove `Audio 18_20.peak': No such file or directory
rm: cannot remove `Audio 19_00.peak': No such file or directory
rm: cannot remove `Audio 19_01.peak': No such file or directory
rm: cannot remove `Audio 19_02.peak': No such file or directory
```

```
gabriele@gabriele-System-Product-Name:/media/EXTERNAL/coppa/Progetti Cubase/piano2/Images$ dir
Audio\ 11_20.peak  Audio\ 14_09.peak  Audio\ 15_14.peak  Audio\ 16_11.peak  Audio\ 18_05.peak
Audio\ 13_29.peak  Audio\ 14_10.peak  Audio\ 15_15.peak  Audio\ 16_12.peak  Audio\ 18_06.peak
Audio\ 13_30.peak  Audio\ 14_11.peak  Audio\ 15_16.peak  Audio\ 16_13.peak  Audio\ 18_08.peak
Audio\ 13_31.peak  Audio\ 14_12.peak  Audio\ 15_17.peak  Audio\ 16_14.peak  Audio\ 18_09.peak
Audio\ 13_32.peak  Audio\ 14_13.peak  Audio\ 15_18.peak  Audio\ 16_15.peak  Audio\ 18_10.peak
Audio\ 13_33.peak  Audio\ 14_14.peak  Audio\ 15_19.peak  Audio\ 16_16.peak  Audio\ 18_11.peak
Audio\ 13_34.peak  Audio\ 14_15.peak  Audio\ 15_20.peak  Audio\ 16_18.peak  Audio\ 18_12.peak
Audio\ 13_35.peak  Audio\ 15_00.peak  Audio\ 15_21.peak  Audio\ 16_19.peak  Audio\ 18_13.peak
Audio\ 13_36.peak  Audio\ 15_01.peak  Audio\ 15_22.peak  Audio\ 16_20.peak  Audio\ 18_14.peak
Audio\ 13_37.peak  Audio\ 15_02.peak  Audio\ 15_23.peak  Audio\ 17_00.peak  Audio\ 18_15.peak
Audio\ 13_38.peak  Audio\ 15_03.peak  Audio\ 16_01.peak  Audio\ 17_01.peak  Audio\ 18_16.peak
Audio\ 13_39.peak  Audio\ 15_04.peak  Audio\ 16_02.peak  Audio\ 17_02.peak  Audio\ 18_17.peak
Audio\ 14_00.peak  Audio\ 15_05.peak  Audio\ 16_03.peak  Audio\ 17_03.peak  Audio\ 18_18.peak
Audio\ 14_01.peak  Audio\ 15_06.peak  Audio\ 16_04.peak  Audio\ 17_04.peak  Audio\ 18_19.peak
Audio\ 14_02.peak  Audio\ 15_08.peak  Audio\ 16_05.peak  Audio\ 17_05.peak  Audio\ 18_20.peak
Audio\ 14_03.peak  Audio\ 15_09.peak  Audio\ 16_06.peak  Audio\ 18_00.peak  Audio\ 19_00.peak
Audio\ 14_04.peak  Audio\ 15_10.peak  Audio\ 16_07.peak  Audio\ 18_01.peak  Audio\ 19_01.peak
Audio\ 14_05.peak  Audio\ 15_11.peak  Audio\ 16_08.peak  Audio\ 18_02.peak  Audio\ 19_02.peak
Audio\ 14_07.peak  Audio\ 15_12.peak  Audio\ 16_09.peak  Audio\ 18_03.peak
Audio\ 14_08.peak  Audio\ 15_13.peak  Audio\ 16_10.peak  Audio\ 18_04.peak

```

Sounds crazy to me. Thanks anyway for your help whether I receive it or not.

---

