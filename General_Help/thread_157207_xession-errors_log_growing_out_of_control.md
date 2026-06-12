---
title: "xession-errors log growing out of control"
date: 2006-04-08
forum: General Help
---

### Post by usergentoo on 2006-04-08
I have constant disk access every 5 seconds it happens on  breezy and dapper. Ive tracked it down to my xsession-errors log. On my desktop Im using breezy and the log is around 4 gb. On my laptop using dapper its about 40 mb since my last reboot less then a couple of hours ago. Couldnt post both logs and it would only post part of one.

```
Xsession: X session started for bigbilly at Sat Apr  8 16:45:46 EDT 2006
startkde: Starting up...
kbuildsycoca running...
kded: Launching previous backup analyse.
Predefined macro file '/usr/lib/gcc/i486-linux-gnu/4.0.3/include/mcpp_gcc40_predef_old.h' is not found
Predefined macro file '/usr/lib/gcc/i486-linux-gnu/4.0.3/include/mcpp_gcc40_predef_std.h' is not found
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/kde3/kcm_kdnssd.so: undefined symbol: init_kdnssd
kbuildsycoca running...
Reusing existing ksycoca
kbluetoothd: HciListener::HciListener()
kbluetoothd: WARNING: No usable bluetooth device found.
kbluetoothd: Using hci0 as default bluetooth device.
kbluetoothd: TrayIcon::slotMruMenuUpdate
kbluetoothd: Kbluetoothd: Error opening HCI socket
kbluetoothd: TrayIcon::slotMruMenuUpdate
ScimInputContextPlugin()
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2400059
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2400059
Ignored duplicate item: Firefox
ScimInputContextPlugin()
trying '/home/bigbilly/.xcompmgrrc' as configfile


finished parsing the config file
error 8 request 153 minor 4 serial 604
error 177 request 153 minor 8 serial 605
error 177 request 153 minor 8 serial 642
error 177 request 153 minor 8 serial 684
error 177 request 153 minor 8 serial 726
error 177 request 153 minor 8 serial 768
error 177 request 153 minor 8 serial 810
error 177 request 153 minor 8 serial 852
error 177 request 153 minor 8 serial 894
error 177 request 153 minor 8 serial 936
error 177 request 153 minor 8 serial 978
error 177 request 153 minor 8 serial 1020
error 177 request 153 minor 8 serial 1062
error 177 request 153 minor 8 serial 1104
error 177 request 153 minor 8 serial 1126
error 177 request 153 minor 8 serial 1164
error 177 request 153 minor 8 serial 1206
error 177 request 153 minor 8 serial 1248
error 177 request 153 minor 8 serial 1290
error 177 request 153 minor 8 serial 1332
error 177 request 153 minor 8 serial 1374
error 177 request 153 minor 8 serial 1416
error 177 request 153 minor 8 serial 1458
error 177 request 153 minor 8 serial 1500
error 177 request 153 minor 8 serial 1542
error 177 request 153 minor 8 serial 1584
error 177 request 153 minor 8 serial 1626
error 177 request 153 minor 8 serial 1668
error 177 request 153 minor 8 serial 1710
error 177 request 153 minor 8 serial 1752
error 177 request 153 minor 8 serial 1794
error 177 request 153 minor 8 serial 1836
error 177 request 153 minor 8 serial 1878
error 177 request 153 minor 8 serial 1920
error 177 request 153 minor 8 serial 1962
error 177 request 153 minor 8 serial 2007
error 177 request 153 minor 8 serial 2025
error 177 request 153 minor 8 serial 2043
error 177 request 153 minor 8 serial 2187
error 177 request 153 minor 8 serial 2230
error 177 request 153 minor 8 serial 2255
error 177 request 153 minor 8 serial 2284
error 177 request 153 minor 8 serial 2478
error 177 request 153 minor 8 serial 2496
error 177 request 153 minor 8 serial 2514
error 177 request 153 minor 7 serial 2523
error 3 request 20 minor 0 serial 10795
error 175 request 151 minor 14 serial 40650
error 175 request 151 minor 14 serial 40656
error 175 request 151 minor 14 serial 40812
error 175 request 151 minor 14 serial 40822
error 175 request 151 minor 14 serial 40978
error 175 request 151 minor 14 serial 40988
error 175 request 151 minor 14 serial 41107
error 175 request 151 minor 14 serial 41117
error 175 request 151 minor 14 serial 41129
error 175 request 151 minor 14 serial 41135
error 175 request 151 minor 14 serial 41195
error 175 request 151 minor 14 serial 41201
error 175 request 151 minor 14 serial 41213
error 175 request 151 minor 14 serial 41219
error 175 request 151 minor 14 serial 41370
error 175 request 151 minor 14 serial 41380
error 175 request 151 minor 14 serial 41400
error 175 request 151 minor 14 serial 41410
error 175 request 151 minor 14 serial 41561
error 175 request 151 minor 14 serial 41571
error 175 request 151 minor 14 serial 41591
error 175 request 151 minor 14 serial 41601
error 175 request 151 minor 14 serial 41725
error 175 request 151 minor 14 serial 41731
error 175 request 151 minor 14 serial 41743
error 175 request 151 minor 14 serial 41749
error 175 request 151 minor 14 serial 41896
error 175 request 151 minor 14 serial 41906
error 175 request 151 minor 14 serial 41926
error 175 request 151 minor 14 serial 41936
error 175 request 151 minor 14 serial 42087
error 175 request 151 minor 14 serial 42097
error 175 request 151 minor 14 serial 42117
error 175 request 151 minor 14 serial 42127
error 175 request 151 minor 14 serial 42278
error 175 request 151 minor 14 serial 42288
error 175 request 151 minor 14 serial 42308
error 175 request 151 minor 14 serial 42318
error 175 request 151 minor 14 serial 42440
error 175 request 151 minor 14 serial 42446
error 175 request 151 minor 14 serial 42458
error 175 request 151 minor 14 serial 42464
error 175 request 151 minor 14 serial 53442
error 175 request 151 minor 14 serial 53479
error 175 request 151 minor 14 serial 53529
error 175 request 151 minor 14 serial 53578
error 175 request 151 minor X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
konsole: WARNING: Unable to use /usr/share/apps/konsole/mc.desktop
konsole: WARNING: Unable to use /usr/share/apps/konsole/sumc.desktop
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
14 serial 53627
error 175 request 151 minor 14 serial 53676
error 175 request 151 minor 14 serial 53725
error 175 request 151 minor 14 serial 53774
error 175 request 151 minor 14 serial 53811
error 175 request 151 minor 14 serial 53848
error 175 request 151 minor 14 serial 53897
error 175 request 151 minor 14 serial 53934
error 175 request 151 minor 14 serial 53983
error 175 request 151 minor 14 serial 54020
error 175 request 151 minor 14 serial 54069
error 175 request 151 minor 14 serial 54118
error 175 request 151 minor 14 serial 54167
error 175 request 151 minor 14 serial 54216
error 175 request 151 minor 14 serial 54265
error 3 request 20 minor 0 serial 67955
error 3 request 20 minor 0 serial 71567
error 3 request 20 minor 0 serial 75133
error 3 request 20 minor 0 serial 82740
error 3 request 20 minor 0 serial 86270
error 3 request 20 minor 0 serial 90040
error 3 request 20 minor 0 serial 97456
error 3 request 20 minor 0 serial 100911
error 3 request 20 minor 0 serial 143065
error 3 request 20 minor 0 serial 148741
error 9 request 156 minor 1 serial 155540
error 3 request 128 minor 6 serial 155541
error 3 request 20 minor 0 serial 155542
error 3 request 20 minor 0 serial 155543
error 3 request 20 minor 0 serial 155544
error 3 request 20 minor 0 serial 155545
error 3 request 20 minor 0 serial 155546
error 3 request 20 minor 0 serial 155547
error 3 request 15 minor 0 serial 155548
error 3 request 20 minor 0 serial 155642
error 3 request 20 minor 0 serial 155643
error 3 request 20 minor 0 serial 155644
error 3 request 20 minor 0 serial 155645
error 3 request 20 minor 0 serial 155646
error 3 request 15 minor 0 serial 155647
error 9 request 156 minor 1 serial 155963
error 3 request 128 minor 6 serial 155964
error 3 request 20 minor 0 serial 155965
error 3 request 20 minor 0 serial 155966
error 3 request 20 minor 0 serial 155967
error 3 request 20 minor 0 serial 155968
error 3 request 20 minor 0 serial 155969
error 3 request 20 minor 0 serial 155970
error 3 request 15 minor 0 serial 155971
error 9 request 156 minor 1 serial 156705
error 3 request 128 minor 6 serial 156706
error 3 request 20 minor 0 serial 156707
error 3 request 20 minor 0 serial 156708
error 3 request 20 minor 0 serial 156709
error 3 request 20 minor 0 serial 156710
error 3 request 20 minor 0 serial 156711
error 3 request 20 minor 0 serial 156712
error 3 request 15 minor 0 serial 156713
error 9 request 156 minor 1 serial 157479
error 3 request 128 minor 6 serial 157480
error 3 request 20 minor 0 serial 157481
error 3 request 20 minor 0 serial 157482
error 3 request 20 minor 0 serial 157483
error 3 request 20 minor 0 serial 157484
error 3 request 20 minor 0 serial 157485
error 3 request 20 minor 0 serial 157486
error 3 request 15 minor 0 serial 157487
error 3 request 20 minor 0 serial 157497
error 3 request 20 minor 0 serial 157498
error 3 request 15 minor 0 serial 157499
error 3 request 20 minor 0 serial 159311
error 3 request 15 minor 0 serial 159312
error 3 request 20 minor 0 serial 160690
error 3 request 20 minor 0 serial 160691
error 3 request 15 minor 0 serial 160692
error 9 request 156 minor 1 serial 163926
error 3 request 128 minor 6 serial 163927
error 3 request 20 minor 0 serial 163928
error 3 request 20 minor 0 serial 163929
error 3 request 20 minor 0 serial 163930
error 3 request 20 minor 0 serial 163931
error 3 request 20 minor 0 serial 163932
error 3 request 20 minor 0 serial 163933
error 3 request 15 minor 0 serial 163934
error 9 request 156 minor 1 serial 163950
error 3 request 128 minor 6 serial 163951
error 3 request 20 minor 0 serial 163952
error 3 request 20 minor 0 serial 163953
error 3 request 20 minor 0 serial 163954
error 3 request 20 minor 0 serial 163955
error 3 request 20 minor 0 serial 163956
error 3 request 20 minor 0 serial 163957
error 3 request 15 minor 0 serial 163958
error 9 request 156 minor 1 serial 166374
error 3 request 128 minor 6 serial 166375
error 3 request 20 minor 0 serial 166376
error 3 request 20 minor 0 serial 166377
error 3 request 20 minor 0 serial 166378
error 3 request 20 minor 0 serial 166379
error 3 request 20 minor 0 serial 166380
error 3 request 20 minor 0 serial 166381
error 3 request 15 minor 0 serial 166382
error 9 request 156 minor 1 serial 166403
error 3 request 128 minor 6 serial 166404
error 3 request 20 minor 0 serial 166405
error 3 request 20 minor 0 serial 166406
error 3 request 20 minor 0 serial 166407
error 3 request 20 minor 0 serial 166408
error 3 request 20 minor 0 serial 166409
error 3 request 20 minor 0 serial 166410
error 3 request 15 minor 0 serial 166411
error 9 request 156 minor 1 serial 166420
error 3 request 128 minor 6 serial 166421
error 3 request 20 minor 0 serial 166422
error 3 request 20 minor 0 serial 166423
error 3 request 20 minor 0 serial 166424
error 3 request 20 minor 0 serial 166425
error 3 request 20 minor 0 serial 166426
error 3 request 20 minor 0 serial 166427
error 3 request 15 minor 0 serial 166428
error 9 request 156 minor 1 serial 166498
error 3 request 128 minor 6 serial 166499
error 3 request 20 minor 0 serial 166500
error 3 request 20 minor 0 serial 166501
error 3 request 20 minor 0 serial 166502
error 3 request 20 minor 0 serial 166503
error 3 request 20 minor 0 serial 166504
error 3 request 20 minor 0 serial 166505
error 3 request 15 minor 0 serial 166506
error 9 request 156 minor 1 serial 166736
error 3 request 128 minor 6 serial 166737
error 3 request 20 minor 0 serial 166738
error 3 request 20 minor 0 serial 166739
error 3 request 20 minor 0 serial 166740
error 3 request 20 minor 0 serial 166741
error 3 request 20 minor 0 serial 166742
error 3 request 20 minor 0 serial 166743
error 3 request 15 minor 0 serial 166744
error 9 request 156 minor 1 serial 166962
error 3 request 128 minor 6 serial 166963
error 3 request 20 minor 0 serial 166964
error 3 request 20 minor 0 serial 166965
error 3 request 20 minor 0 serial 166966
error 3 request 20 minor 0 serial 166967
error 3 request 20 minor 0 serial 166968
error 3 request 20 minor 0 serial 166969
error 3 request 15 minor 0 serial 166970
error 9 request 156 minor 1 serial 167239
error 3 request 128 minor 6 serial 167240
error 3 request 20 minor 0 serial 167241
error 3 request 20 minor 0 serial 167242
error 3 request 20 minor 0 serial 167243
error 3 request 20 minor 0 serial 167244
error 3 request 20 minor 0 serial 167245
error 3 request 20 minor 0 serial 167246
error 3 request 15 minor 0 serial 167247
error 3 request 20 minor 0 serial 167543
error 3 request 20 minor 0 serial 167544
error 3 request 20 minor 0 serial 167545
error 3 request 20 minor 0 serial 167546
error 3 request 20 minor 0 serial 167547
error 3 request 15 minor 0 serial 167548
error 3 request 20 minor 0 serial 167715
error 3 request 20 minor 0 serial 167716
error 3 request 20 minor 0 serial 167717
error 3 request 20 minor 0 serial 167718
error 3 request 15 minor 0 serial 167719
error 3 request 20 minor 0 serial 167885
error 3 request 20 minor 0 serial 167886
error 3 request 20 minor 0 serial 167887
error 3 request 20 minor 0 serial 167888
error 3 request 20 minor 0 serial 167889
error 3 request 15 minor 0 serial 167890
error 3 request 20 minor 0 serial 168003
error 3 request 20 minor 0 serial 168004
error 3 request 20 minor 0 serial 168005
error 3 request 20 minor 0 serial 168006
error 3 request 20 minor 0 serial 168007
error 3 request 15 minor 0 serial 168008
error 3 request 20 minor 0 serial 168073
error 3 request 20 minor 0 serial 168074
error 3 request 20 minor 0 serial 168075
error 3 request 20 minor 0 serial 168076
error 3 request 20 minor 0 serial 168077
error 3 request 15 minor 0 serial 168078
error 9 request 156 minor 1 serial 168306
error 3 request 128 minor 6 serial 168307
error 3 request 20 minor 0 serial 168308
error 3 request 20 minor 0 serial 168309
error 3 request 20 minor 0 serial 168310
error 3 request 20 minor 0 serial 168311
error 3 request 20 minor 0 serial 168312
error 3 request 20 minor 0 serial 168313
error 3 request 15 minor 0 serial 168314
error 3 request 20 minor 0 serial 168427
error 3 request 20 minor 0 serial 168428
error 3 request 20 minor 0 serial 168429
error 3 request 20 minor 0 serial 168430
error 3 request 20 minor 0 serial 168431
error 3 request 15 minor 0 serial 168432
error 3 request 20 minor 0 serial 168614
error 3 request 20 minor 0 serial 171569
error 3 request 20 minor 0 serial 171570
error 3 request 20 minor 0 serial 171571
error 3 request 20 minor 0 serial 171572
error 3 request 20 minor 0 serial 171573
error 3 request 15 minor 0 serial 171574
error 3 request 20 minor 0 serial 171707
error 3 request 20 minor 0 serial 171708
error 3 request 15 minor 0 serial 171709
error 9 request 156 minor 1 serial 172289
error 3 request 128 minor 6 serial 172290
error 3 request 20 minor 0 serial 172291
error 3 request 20 minor 0 serial 172292
error 3 request 20 minor 0 serial 172293
error 3 request 20 minor 0 serial 172294
error 3 request 20 minor 0 serial 172295
error 3 request 20 minor 0 serial 172296
error 3 request 15 minor 0 serial 172297
error 9 request 156 minor 1 serial 172548
error 3 request 128 minor 6 serial 172549
error 3 request 20 minor 0 serial 172550
error 3 request 20 minor 0 serial 172551
error 3 request 20 minor 0 serial 172552
error 3 request 20 minor 0 serial 172553
error 3 request 20 minor 0 serial 172554
error 3 request 20 minor 0 serial 172555
error 3 request 15 minor 0 serial 172556
error 9 request 156 minor 1 serial 172564
error 3 request 128 minor 6 serial 172565
error 3 request 20 minor 0 serial 172566
error 3 request 20 minor 0 serial 172567
error 3 request 20 minor 0 serial 172568
error 3 request 20 minor 0 serial 172569
error 3 request 20 minor 0 serial 172570
error 3 request 20 minor 0 serial 172571
error 3 request 15 minor 0 serial 172572
error 9 request 156 minor 1 serial 172629
error 3 request 128 minor 6 serial 172630
error 3 request 20 minor 0 serial 172631
error 3 request 20 minor 0 serial 172632
error 3 request 20 minor 0 serial 172633
error 3 request 20 minor 0 serial 172634
error 3 request 20 minor 0 serial 172635
error 3 request 20 minor 0 serial 172636
error 3 request 15 minor 0 serial 172637
error 3 request 20 minor 0 serial 172810
error 3 request 15 minor 0 serial 172811
error 9 request 156 minor 1 serial 172967
error 3 request 128 minor 6 serial 172968
error 3 request 20 minor 0 serial 172969
error 3 request 20 minor 0 serial 172970
error 3 request 20 minor 0 serial 172971
error 3 request 20 minor 0 serial 172972
error 3 request 20 minor 0 serial 172973
error 3 request 20 minor 0 serial 172974
error 3 request 15 minor 0 serial 172975
error 3 request 15 minor 0 serial 173152
error 3 request 20 minor 0 serial 173270
error 3 request 20 minor 0 serial 173271
error 3 request 20 minor 0 serial 173272
error 3 request 15 minor 0 serial 173273
error 9 request 156 minor 1 serial 173723
error 3 request 128 minor 6 serial 173724
error 3 request 20 minor 0 serial 173725
error 3 request 20 minor 0 serial 173726
error 3 request 20 minor 0 serial 173727
error 3 request 20 minor 0 serial 173728
error 3 request 20 minor 0 serial 173729
error 3 request 20 minor 0 serial 173730
error 3 request 15 minor 0 serial 173731
error 9 request 156 minor 1 serial 173794
error 3 request 128 minor 6 serial 173795
error 3 request 20 minor 0 serial 173796
error 3 request 20 minor 0 serial 173797
error 3 request 20 minor 0 serial 173798
error 3 request 20 minor 0 serial 173799
error 3 request 20 minor 0 serial 173800
error 3 request 20 minor 0 serial 173801
error 3 request 15 minor 0 serial 173802
error 3 request 20 minor 0 serial 173985
error 3 request 20 minor 0 serial 173986
error 3 request 20 minor 0 serial 173987
error 3 request 20 minor 0 serial 173988
error 3 request 20 minor 0 serial 173989
error 3 request 15 minor 0 serial 173990
error 9 request 156 minor 1 serial 174049
error 3 request 128 minor 6 serial 174050
error 3 request 20 minor 0 serial 174051
error 3 request 20 minor 0 serial 174052
error 3 request 20 minor 0 serial 174053
error 3 request 20 minor 0 serial 174054
error 3 request 20 minor 0 serial 174055
error 3 request 20 minor 0 serial 174056
error 3 request 15 minor 0 serial 174057
error 9 request 156 minor 1 serial 174061
error 3 request 128 minor 6 serial 174062
error 3 request 20 minor 0 serial 174063
error 3 requesX Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3401470
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x340009f
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3a00013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x4000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x3000013
~ScimInputContextPlugin()
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x800007
ScimInputContextPlugin()
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0xc00061
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
QFont::setPixelSize: Pixel size <= 0 (0)
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
t 20 minor 0 serial 174064
error 3 request 20 minor 0 serial 174065
error 3 request 20 minor 0 serial 174066
error 3 request 20 minor 0 serial 174067
error 3 request 20 minor 0 serial 174068
error 3 request 15 minor 0 serial 174069
error 3 request 20 minor 0 serial 174343
error 3 request 20 minor 0 serial 174344
error 3 request 20 minor 0 serial 174345
error 3 request 15 minor 0 serial 174346
error 9 request 156 minor 1 serial 174500
error 3 request 128 minor 6 serial 174501
error 3 request 20 minor 0 serial 174502
error 3 request 20 minor 0 serial 174503
error 3 request 20 minor 0 serial 174504
error 3 request 20 minor 0 serial 174505
error 3 request 20 minor 0 serial 174506
error 3 request 20 minor 0 serial 174507
error 3 request 15 minor 0 serial 174508
error 3 request 15 minor 0 serial 174579
error 9 request 156 minor 1 serial 174788
error 3 request 128 minor 6 serial 174789
error 3 request 20 minor 0 serial 174790
error 3 request 20 minor 0 serial 174791
error 3 request 20 minor 0 serial 174792
error 3 request 20 minor 0 serial 174793
error 3 request 20 minor 0 serial 174794
error 3 request 20 minor 0 serial 174795
error 3 request 15 minor 0 serial 174796
error 3 request 20 minor 0 serial 184097
error 3 request 20 minor 0 serial 188315
error 175 request 151 minor 14 serial 188524
error 3 request 20 minor 0 serial 199907
error 3 request 20 minor 0 serial 199918
error 3 request 20 minor 0 serial 206160
error 175 request 151 minor 14 serial 206369
error 175 request 151 minor 14 serial 206422
error 3 request 20 minor 0 serial 208302
error 3 request 20 minor 0 serial 210735
error 3 request 20 minor 0 serial 215912
error 175 request 151 minor 14 serial 216780
error 175 request 151 minor 14 serial 216850
error 175 request 151 minor 14 serial 216928
error 175 request 151 minor 14 serial 216998
error 175 request 151 minor 14 serial 217072
error 175 request 151 minor 14 serial 217146
error 175 request 151 minor 14 serial 217220
error 175 request 151 minor 14 serial 217269
error 175 request 151 minor 14 serial 217339
error 175 request 151 minor 14 serial 217413
error 175 request 151 minor 14 serial 217487
error 175 request 151 minor 14 serial 217561
error 3 request 20 minor 0 serial 221398
error 3 request 20 minor 0 serial 231326
error 3 request 20 minor 0 serial 235016
error 3 request 20 minor 0 serial 238909
error 3 request 20 minor 0 serial 243028
error 3 request 20 minor 0 serial 247108
error 3 request 20 minor 0 serial 250987
error 3 request 20 minor 0 serial 255101
error 3 request 20 minor 0 serial 258773
error 3 request 20 minor 0 serial 267371
error 3 request 20 minor 0 serial 293132
error 3 request 20 minor 0 serial 309256
error 3 request 20 minor 0 serial 309267
error 3 request 20 minor 0 serial 317455
error 3 request 20 minor 0 serial 320737
error 3 request 20 minor 0 serial 324289
error 3 request 20 minor 0 serial 327781
error 3 request 20 minor 0 serial 332388
error 3 request 20 minor 0 serial 332399
error 3 request 20 minor 0 serial 341105
error 3 request 20 minor 0 serial 341116
error 3 request 20 minor 0 serial 341485
error 175 request 151 minor 14 serial 341676
error 175 request 151 minor 14 serial 341705
error 175 request 151 minor 14 serial 341734
error 9 request 156 minor 1 serial 343395
error 3 request 128 minor 6 serial 343396
error 3 request 20 minor 0 serial 343397
error 3 request 20 minor 0 serial 343398
error 3 request 20 minor 0 serial 343399
error 3 request 20 minor 0 serial 343400
error 3 request 20 minor 0 serial 343401
error 3 request 20 minor 0 serial 343402
error 3 request 15 minor 0 serial 343403
error 3 request 20 minor 0 serial 343641
error 3 request 20 minor 0 serial 343642
error 3 request 15 minor 0 serial 343643
error 175 request 151 minor 14 serial 359838
error 175 request 151 minor 14 serial 359879
error 175 request 151 minor 14 serial 359943
error 175 request 151 minor 14 serial 360011
error 175 request 151 minor 14 serial 360079
error 175 request 151 minor 14 serial 360125
error 175 request 151 minor 14 serial 517491
error 175 request 151 minor 14 serial 517501

```

---

### Post by usergentoo on 2006-04-09
Talked to several other people on irc and they have the same problem, but didnt know what to do. Im sure somebody has an idea to stop this log from growing.

---

