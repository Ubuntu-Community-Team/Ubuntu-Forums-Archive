---
title: "strange log activity"
date: 2010-03-16
forum: General Help
---

### Post by Fika on 2010-03-16
Can someone tell me what is happening to my computer and how to stop this? The hd starts running on it's own and I check the log files and find this: 


```
Mar 16 21:28:47 ubuntu kernel: [16953.273544] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:28:47 ubuntu kernel: [16953.293541] Buffer I/O error on device sr1, logical block 26827
Mar 16 21:28:47 ubuntu kernel: [16953.293550] Buffer I/O error on device sr1, logical block 26828
Mar 16 21:28:47 ubuntu kernel: [16953.293619] Buffer I/O error on device sr1, logical block 26827
Mar 16 21:28:47 ubuntu kernel: [16953.293623] Buffer I/O error on device sr1, logical block 26828
Mar 16 21:28:47 ubuntu kernel: [16953.293645] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:28:47 ubuntu kernel: [16953.293649] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:28:47 ubuntu kernel: [16953.293652] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:28:47 ubuntu kernel: [16953.293705] Buffer I/O error on device sr1, logical block 26827
Mar 16 21:28:47 ubuntu kernel: [16953.293708] Buffer I/O error on device sr1, logical block 26828
Mar 16 21:28:47 ubuntu kernel: [16953.293747] Buffer I/O error on device sr1, logical block 26829
Mar 16 21:28:47 ubuntu kernel: [16953.293750] Buffer I/O error on device sr1, logical block 26830
Mar 16 21:28:47 ubuntu kernel: [16953.293753] Buffer I/O error on device sr1, logical block 26831
Mar 16 21:28:47 ubuntu kernel: [16953.293756] Buffer I/O error on device sr1, logical block 26832
Mar 16 21:28:47 ubuntu kernel: [16953.294486] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:28:47 ubuntu kernel: [16953.294489] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:28:47 ubuntu kernel: [16953.294492] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:28:47 ubuntu kernel: [16953.294558] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:28:47 ubuntu kernel: [16953.294560] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:28:47 ubuntu kernel: [16953.294563] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:28:47 ubuntu kernel: [16953.295073] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:28:47 ubuntu kernel: [16953.295075] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:28:47 ubuntu kernel: [16953.295078] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:28:47 ubuntu kernel: [16953.295682] SQUASHFS error: sb_bread failed reading block 0xaa584
Mar 16 21:28:47 ubuntu kernel: [16953.295685] SQUASHFS error: Unable to read cache block [2a961367:1b43]
Mar 16 21:28:47 ubuntu kernel: [16953.295705] SQUASHFS error: Unable to read inode [2a961367:1b43]
Mar 16 21:28:47 ubuntu kernel: [16953.295764] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:28:47 ubuntu kernel: [16953.306163] SQUASHFS error: sb_bread failed reading block 0x2fac
Mar 16 21:28:47 ubuntu kernel: [16953.306170] SQUASHFS error: Unable to read fragment cache block [be4098]
Mar 16 21:28:47 ubuntu kernel: [16953.306173] SQUASHFS error: Unable to read page, block be4098, size 7272
Mar 16 21:28:47 ubuntu kernel: [16953.306746] SQUASHFS error: sb_bread failed reading block 0x2fac
Mar 16 21:28:47 ubuntu kernel: [16953.306749] SQUASHFS error: Unable to read fragment cache block [be4098]
Mar 16 21:28:47 ubuntu kernel: [16953.306752] SQUASHFS error: Unable to read page, block be4098, size 7272
Mar 16 21:28:47 ubuntu kernel: [16953.453647] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:28:47 ubuntu kernel: [16953.633763] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:28:47 ubuntu kernel: [16953.850701] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.850708] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.850712] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.851498] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.851501] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.851504] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.851570] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.851572] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.851575] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.853737] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.853740] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.853743] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.853814] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.853816] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.853819] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.854480] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.854483] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.854486] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.854552] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.854555] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.854557] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.855017] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.855020] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.855023] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.855081] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.855084] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.855086] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.855540] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.855543] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.855545] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.855606] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.855609] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.855612] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.860171] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.860175] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.860177] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.860246] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.860249] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.860251] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.860748] SQUASHFS error: sb_bread failed reading block 0x51328
Mar 16 21:28:47 ubuntu kernel: [16953.860750] SQUASHFS error: Unable to read fragment cache block [144bfec0]
Mar 16 21:28:47 ubuntu kernel: [16953.860753] SQUASHFS error: Unable to read page, block 144bfec0, size a4b3
Mar 16 21:28:47 ubuntu kernel: [16953.863467] SQUASHFS error: sb_bread failed reading block 0x22746
Mar 16 21:28:47 ubuntu kernel: [16953.863473] SQUASHFS error: Unable to read fragment cache block [89c8185]
Mar 16 21:28:47 ubuntu kernel: [16953.863476] SQUASHFS error: Unable to read page, block 89c8185, size 9855
Mar 16 21:28:47 ubuntu kernel: [16953.866249] SQUASHFS error: sb_bread failed reading block 0x22746
Mar 16 21:28:47 ubuntu kernel: [16953.866252] SQUASHFS error: Unable to read fragment cache block [89c8185]
Mar 16 21:28:47 ubuntu kernel: [16953.866255] SQUASHFS error: Unable to read page, block 89c8185, size 9855
Mar 16 21:28:47 ubuntu kernel: [16953.866330] SQUASHFS error: sb_bread failed reading block 0x22746
Mar 16 21:28:47 ubuntu kernel: [16953.866333] SQUASHFS error: Unable to read fragment cache block [89c8185]
Mar 16 21:28:47 ubuntu kernel: [16953.866335] SQUASHFS error: Unable to read page, block 89c8185, size 9855
Mar 16 21:28:47 ubuntu kernel: [16953.866764] SQUASHFS error: sb_bread failed reading block 0x22746
Mar 16 21:28:47 ubuntu kernel: [16953.866767] SQUASHFS error: Unable to read fragment cache block [89c8185]
Mar 16 21:28:47 ubuntu kernel: [16953.866769] SQUASHFS error: Unable to read page, block 89c8185, size 9855
Mar 16 21:28:47 ubuntu kernel: [16953.866839] SQUASHFS error: sb_bread failed reading block 0x22746
Mar 16 21:28:47 ubuntu kernel: [16953.866842] SQUASHFS error: Unable to read fragment cache block [89c8185]
Mar 16 21:28:47 ubuntu kernel: [16953.866844] SQUASHFS error: Unable to read page, block 89c8185, size 9855
Mar 16 21:28:47 ubuntu kernel: [16953.879096] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:28:47 ubuntu kernel: [16953.898314] SQUASHFS error: sb_bread failed reading block 0x227af
Mar 16 21:28:47 ubuntu kernel: [16953.898320] SQUASHFS error: Unable to read fragment cache block [89e12b6]
Mar 16 21:28:47 ubuntu kernel: [16953.898323] SQUASHFS error: Unable to read page, block 89e12b6, size acea
Mar 16 21:28:47 ubuntu kernel: [16953.899452] SQUASHFS error: sb_bread failed reading block 0x227af
Mar 16 21:28:47 ubuntu kernel: [16953.899455] SQUASHFS error: Unable to read fragment cache block [89e12b6]
Mar 16 21:28:47 ubuntu kernel: [16953.899458] SQUASHFS error: Unable to read page, block 89e12b6, size acea
Mar 16 21:28:47 ubuntu kernel: [16953.899523] SQUASHFS error: sb_bread failed reading block 0x227af
Mar 16 21:28:47 ubuntu kernel: [16953.899526] SQUASHFS error: Unable to read fragment cache block [89e12b6]
Mar 16 21:28:47 ubuntu kernel: [16953.899529] SQUASHFS error: Unable to read page, block 89e12b6, size acea
Mar 16 21:28:47 ubuntu kernel: [16953.901918] SQUASHFS error: sb_bread failed reading block 0x227af
Mar 16 21:28:47 ubuntu kernel: [16953.901921] SQUASHFS error: Unable to read fragment cache block [89e12b6]
Mar 16 21:28:47 ubuntu kernel: [16953.901924] SQUASHFS error: Unable to read page, block 89e12b6, size acea
Mar 16 21:28:47 ubuntu kernel: [16953.902000] SQUASHFS error: sb_bread failed reading block 0x227af
Mar 16 21:28:47 ubuntu kernel: [16953.902003] SQUASHFS error: Unable to read fragment cache block [89e12b6]
Mar 16 21:28:47 ubuntu kernel: [16953.902006] SQUASHFS error: Unable to read page, block 89e12b6, size acea
Mar 16 21:28:48 ubuntu kernel: [16954.054051] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:28:48 ubuntu kernel: [16954.055612] SQUASHFS error: sb_bread failed reading block 0xbe5b
Mar 16 21:28:48 ubuntu kernel: [16954.055618] SQUASHFS error: Unable to read fragment cache block [2f8c0b9]
Mar 16 21:28:48 ubuntu kernel: [16954.055621] SQUASHFS error: Unable to read page, block 2f8c0b9, size ae93
Mar 16 21:28:48 ubuntu kernel: [16954.057025] SQUASHFS error: sb_bread failed reading block 0xbe5b
Mar 16 21:28:48 ubuntu kernel: [16954.057029] SQUASHFS error: Unable to read fragment cache block [2f8c0b9]
Mar 16 21:28:48 ubuntu kernel: [16954.057031] SQUASHFS error: Unable to read page, block 2f8c0b9, size ae93
Mar 16 21:28:48 ubuntu kernel: [16954.057102] SQUASHFS error: sb_bread failed reading block 0xbe5b
Mar 16 21:28:48 ubuntu kernel: [16954.057105] SQUASHFS error: Unable to read fragment cache block [2f8c0b9]
Mar 16 21:28:48 ubuntu kernel: [16954.057108] SQUASHFS error: Unable to read page, block 2f8c0b9, size ae93
Mar 16 21:28:48 ubuntu kernel: [16954.057594] SQUASHFS error: sb_bread failed reading block 0xbe5b
Mar 16 21:28:48 ubuntu kernel: [16954.057597] SQUASHFS error: Unable to read fragment cache block [2f8c0b9]
Mar 16 21:28:48 ubuntu kernel: [16954.057599] SQUASHFS error: Unable to read page, block 2f8c0b9, size ae93
Mar 16 21:28:48 ubuntu kernel: [16954.057661] SQUASHFS error: sb_bread failed reading block 0xbe5b
Mar 16 21:28:48 ubuntu kernel: [16954.057664] SQUASHFS error: Unable to read fragment cache block [2f8c0b9]
Mar 16 21:28:48 ubuntu kernel: [16954.057666] SQUASHFS error: Unable to read page, block 2f8c0b9, size ae93
Mar 16 21:28:48 ubuntu kernel: [16954.058271] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:28:48 ubuntu kernel: [16954.058274] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:28:48 ubuntu kernel: [16954.058277] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:28:48 ubuntu kernel: [16954.059136] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:28:48 ubuntu kernel: [16954.059835] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:28:48 ubuntu kernel: [16954.059838] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:28:48 ubuntu kernel: [16954.059841] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:28:48 ubuntu kernel: [16954.059906] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:28:49 ubuntu kernel: [16955.274920] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:28:49 ubuntu kernel: [16955.455033] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:28:51 ubuntu kernel: [16957.276314] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:28:51 ubuntu kernel: [16957.456467] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:28:53 ubuntu kernel: [16959.277717] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:28:53 ubuntu kernel: [16959.457866] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:28:55 ubuntu kernel: [16961.265668] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:28:55 ubuntu kernel: [16961.297299] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:28:55 ubuntu kernel: [16961.431293] SQUASHFS error: sb_bread failed reading block 0x227af
Mar 16 21:28:55 ubuntu kernel: [16961.431301] SQUASHFS error: Unable to read fragment cache block [89e12b6]
Mar 16 21:28:55 ubuntu kernel: [16961.431304] SQUASHFS error: Unable to read page, block 89e12b6, size acea
Mar 16 21:28:55 ubuntu kernel: [16961.722233] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:28:55 ubuntu kernel: [16961.722240] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:28:55 ubuntu kernel: [16961.722244] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:28:55 ubuntu kernel: [16961.722385] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:28:55 ubuntu kernel: [16961.962705] SQUASHFS error: sb_bread failed reading block 0x2fac
Mar 16 21:28:55 ubuntu kernel: [16961.962712] SQUASHFS error: Unable to read fragment cache block [be4098]
Mar 16 21:28:55 ubuntu kernel: [16961.962716] SQUASHFS error: Unable to read page, block be4098, size 7272
Mar 16 21:28:56 ubuntu kernel: [16962.047031] SQUASHFS error: sb_bread failed reading block 0xbe5b
Mar 16 21:28:56 ubuntu kernel: [16962.047038] SQUASHFS error: Unable to read fragment cache block [2f8c0b9]
Mar 16 21:28:56 ubuntu kernel: [16962.047041] SQUASHFS error: Unable to read page, block 2f8c0b9, size ae93
Mar 16 21:28:56 ubuntu kernel: [16962.063088] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:28:56 ubuntu kernel: [16962.063095] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:28:56 ubuntu kernel: [16962.063098] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:28:56 ubuntu kernel: [16962.063239] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:28:56 ubuntu kernel: [16962.063495] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:28:56 ubuntu kernel: [16962.063498] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:28:56 ubuntu kernel: [16962.063501] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:28:56 ubuntu kernel: [16962.063557] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:29:49 ubuntu kernel: [17015.217339] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:29:49 ubuntu kernel: [17015.218723] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:29:49 ubuntu kernel: [17015.218729] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:29:49 ubuntu kernel: [17015.218732] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:29:49 ubuntu kernel: [17015.218847] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:29:49 ubuntu kernel: [17015.222126] SQUASHFS error: sb_bread failed reading block 0x2fac
Mar 16 21:29:49 ubuntu kernel: [17015.222133] SQUASHFS error: Unable to read fragment cache block [be4098]
Mar 16 21:29:49 ubuntu kernel: [17015.222136] SQUASHFS error: Unable to read page, block be4098, size 7272
Mar 16 21:29:49 ubuntu kernel: [17015.397442] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:29:49 ubuntu kernel: [17015.577569] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:29:49 ubuntu kernel: [17015.816096] SQUASHFS error: sb_bread failed reading block 0x227af
Mar 16 21:29:49 ubuntu kernel: [17015.816104] SQUASHFS error: Unable to read fragment cache block [89e12b6]
Mar 16 21:29:49 ubuntu kernel: [17015.816107] SQUASHFS error: Unable to read page, block 89e12b6, size acea
Mar 16 21:29:49 ubuntu kernel: [17015.957846] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:29:50 ubuntu kernel: [17016.082935] SQUASHFS error: sb_bread failed reading block 0xbe5b
Mar 16 21:29:50 ubuntu kernel: [17016.082941] SQUASHFS error: Unable to read fragment cache block [2f8c0b9]
Mar 16 21:29:50 ubuntu kernel: [17016.082944] SQUASHFS error: Unable to read page, block 2f8c0b9, size ae93
Mar 16 21:29:50 ubuntu kernel: [17016.083133] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:29:50 ubuntu kernel: [17016.083136] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:29:50 ubuntu kernel: [17016.083139] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:29:50 ubuntu kernel: [17016.083237] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:29:50 ubuntu kernel: [17016.083509] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:29:50 ubuntu kernel: [17016.083512] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:29:50 ubuntu kernel: [17016.083515] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:29:50 ubuntu kernel: [17016.083571] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:29:51 ubuntu kernel: [17017.278783] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:29:51 ubuntu kernel: [17017.458898] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:29:53 ubuntu kernel: [17019.280182] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:29:53 ubuntu kernel: [17019.460295] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:29:55 ubuntu kernel: [17021.261555] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:29:55 ubuntu kernel: [17021.441668] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:29:57 ubuntu kernel: [17023.036591] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:29:57 ubuntu kernel: [17023.038212] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:29:57 ubuntu kernel: [17023.038218] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:29:57 ubuntu kernel: [17023.038221] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:29:57 ubuntu kernel: [17023.038519] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:29:57 ubuntu kernel: [17023.057870] SQUASHFS error: sb_bread failed reading block 0x227af
Mar 16 21:29:57 ubuntu kernel: [17023.057878] SQUASHFS error: Unable to read fragment cache block [89e12b6]
Mar 16 21:29:57 ubuntu kernel: [17023.057881] SQUASHFS error: Unable to read page, block 89e12b6, size acea
Mar 16 21:29:57 ubuntu kernel: [17023.061741] SQUASHFS error: sb_bread failed reading block 0x2fac
Mar 16 21:29:57 ubuntu kernel: [17023.061748] SQUASHFS error: Unable to read fragment cache block [be4098]
Mar 16 21:29:57 ubuntu kernel: [17023.061751] SQUASHFS error: Unable to read page, block be4098, size 7272
Mar 16 21:29:57 ubuntu kernel: [17023.090341] SQUASHFS error: sb_bread failed reading block 0xbe5b
Mar 16 21:29:57 ubuntu kernel: [17023.090347] SQUASHFS error: Unable to read fragment cache block [2f8c0b9]
Mar 16 21:29:57 ubuntu kernel: [17023.090350] SQUASHFS error: Unable to read page, block 2f8c0b9, size ae93
Mar 16 21:29:57 ubuntu kernel: [17023.090530] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:29:57 ubuntu kernel: [17023.090533] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:29:57 ubuntu kernel: [17023.090536] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:29:57 ubuntu kernel: [17023.090623] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:29:57 ubuntu kernel: [17023.090879] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:29:57 ubuntu kernel: [17023.090883] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:29:57 ubuntu kernel: [17023.090885] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:29:57 ubuntu kernel: [17023.090939] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:30:37 ubuntu kernel: [17063.271136] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:30:37 ubuntu kernel: [17063.272884] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:30:37 ubuntu kernel: [17063.272890] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:30:37 ubuntu kernel: [17063.272893] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:30:37 ubuntu kernel: [17063.273008] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:30:37 ubuntu kernel: [17063.275533] SQUASHFS error: sb_bread failed reading block 0x2fac
Mar 16 21:30:37 ubuntu kernel: [17063.275540] SQUASHFS error: Unable to read fragment cache block [be4098]
Mar 16 21:30:37 ubuntu kernel: [17063.275543] SQUASHFS error: Unable to read page, block be4098, size 7272
Mar 16 21:30:37 ubuntu kernel: [17063.451230] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:30:37 ubuntu kernel: [17063.631356] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:30:37 ubuntu kernel: [17063.867203] SQUASHFS error: sb_bread failed reading block 0x227af
Mar 16 21:30:37 ubuntu kernel: [17063.867210] SQUASHFS error: Unable to read fragment cache block [89e12b6]
Mar 16 21:30:37 ubuntu kernel: [17063.867214] SQUASHFS error: Unable to read page, block 89e12b6, size acea
Mar 16 21:30:38 ubuntu kernel: [17064.031636] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:30:38 ubuntu kernel: [17064.098546] SQUASHFS error: sb_bread failed reading block 0xbe5b
Mar 16 21:30:38 ubuntu kernel: [17064.098552] SQUASHFS error: Unable to read fragment cache block [2f8c0b9]
Mar 16 21:30:38 ubuntu kernel: [17064.098555] SQUASHFS error: Unable to read page, block 2f8c0b9, size ae93
Mar 16 21:30:38 ubuntu kernel: [17064.098739] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:30:38 ubuntu kernel: [17064.098742] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:30:38 ubuntu kernel: [17064.098745] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:30:38 ubuntu kernel: [17064.098844] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:30:38 ubuntu kernel: [17064.108290] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:30:38 ubuntu kernel: [17064.108296] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:30:38 ubuntu kernel: [17064.108299] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:30:38 ubuntu kernel: [17064.108425] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:30:39 ubuntu kernel: [17065.272497] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:30:39 ubuntu kernel: [17065.452616] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:30:41 ubuntu kernel: [17067.273911] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:30:41 ubuntu kernel: [17067.454037] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:30:43 ubuntu kernel: [17069.275304] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:30:43 ubuntu kernel: [17069.455420] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:30:45 ubuntu kernel: [17071.276690] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:30:45 ubuntu kernel: [17071.456824] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:30:47 ubuntu kernel: [17073.010803] VFS: busy inodes on changed media or resized disk sr1
Mar 16 21:30:47 ubuntu kernel: [17073.012726] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:30:47 ubuntu kernel: [17073.012732] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:30:47 ubuntu kernel: [17073.012735] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:30:47 ubuntu kernel: [17073.013315] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:30:47 ubuntu kernel: [17073.031546] SQUASHFS error: sb_bread failed reading block 0x227af
Mar 16 21:30:47 ubuntu kernel: [17073.031553] SQUASHFS error: Unable to read fragment cache block [89e12b6]
Mar 16 21:30:47 ubuntu kernel: [17073.031557] SQUASHFS error: Unable to read page, block 89e12b6, size acea
Mar 16 21:30:47 ubuntu kernel: [17073.037098] SQUASHFS error: sb_bread failed reading block 0x2fac
Mar 16 21:30:47 ubuntu kernel: [17073.037105] SQUASHFS error: Unable to read fragment cache block [be4098]
Mar 16 21:30:47 ubuntu kernel: [17073.037108] SQUASHFS error: Unable to read page, block be4098, size 7272
Mar 16 21:30:47 ubuntu kernel: [17073.065547] SQUASHFS error: sb_bread failed reading block 0xbe5b
Mar 16 21:30:47 ubuntu kernel: [17073.065553] SQUASHFS error: Unable to read fragment cache block [2f8c0b9]
Mar 16 21:30:47 ubuntu kernel: [17073.065556] SQUASHFS error: Unable to read page, block 2f8c0b9, size ae93
Mar 16 21:30:47 ubuntu kernel: [17073.065740] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:30:47 ubuntu kernel: [17073.065743] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:30:47 ubuntu kernel: [17073.065745] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:30:47 ubuntu kernel: [17073.065835] Core dump to |/usr/share/apport/apport pipe failed
Mar 16 21:30:47 ubuntu kernel: [17073.066084] SQUASHFS error: sb_bread failed reading block 0xcb75
Mar 16 21:30:47 ubuntu kernel: [17073.066087] SQUASHFS error: Unable to read fragment cache block [32d1bc4]
Mar 16 21:30:47 ubuntu kernel: [17073.066090] SQUASHFS error: Unable to read page, block 32d1bc4, size bba4
Mar 16 21:30:47 ubuntu kernel: [17073.066145] Core dump to |/usr/share/apport/apport pipe failed
```

---

### Post by joberly on 2010-03-16
I don't believe this should be in the security forum.

Have you tried the suggestions on this page?

[https://help.ubuntu.com/community/SquashfsErrors]("https://help.ubuntu.com/community/SquashfsErrors")

---

### Post by Fika on 2010-03-16
Thanks for the reply. I looked at that page but the thing is this is happening after I have already been booted and working for hours with no problems. I thought it was a security issue since the computer just starts going haywire on it's own out of nowhere.

---

### Post by DawieS on 2010-03-16
That log looks a lot like what was called a "**Head Crash**" in the old days when we still worked with those large disks, packed in layers.

I would recommend that you update your backups (or rather take a complete new copy type backup (I have once overwritten a perfectly good backup with partial garbage)), and run a full surface scan on the disk.](*,)

---

### Post by dcstar on 2010-03-16
> **DawieS said:**
> 
..........
I would recommend that you update your backups (or rather take a complete new copy type backup (I have once overwritten a perfectly good backup with partial garbage)), and run a full surface scan on the disk.](*,)

A SMART test of the hard disk may also reveal possible problems - like it may be about to die.......

---

