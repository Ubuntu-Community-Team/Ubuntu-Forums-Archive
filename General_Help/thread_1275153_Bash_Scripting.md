---
title: "Bash Scripting :\"
date: 2009-09-25
forum: General Help
---

### Post by Elfo33 on 2009-09-25
I'm hoping someone can help me with a simple Bash script.  I'd like to clean a simple text file of unneeded entires, for instance, take a redump.org DAT:

```
clrmamepro (
	name "Sega - Mega-CD / Sega CD"
	description "Sega - Mega-CD / Sega CD (111)"
	category Console
	version "20090824 13-46-39"
	author "redump.org"
)

game (
	name "After Burner III (Japan)"
	description "After Burner III (Japan)"
	rom ( name "After Burner III (Japan).cue" size 1410 crc f16b55f2 md5 dc4ea50d994836eb1f08e69df93ad97b sha1 cbc0c1f77abc165505aef0e8e7274557a32d459f )
	rom ( name "After Burner III (Japan) (Track 01).bin" size 7890960 crc 069f1cbb md5 83823b83fad5a100c0736e94da6a00e7 sha1 7c953b026a90ff857444ae40b6455cfb3e23e3f5 )
	rom ( name "After Burner III (Japan) (Track 02).bin" size 12460896 crc 0dd28f10 md5 949669f9e456f5a163cacaa690cb6a87 sha1 480c553f83a18dcd2994a38e4cc51b29e073973c )
	rom ( name "After Burner III (Japan) (Track 03).bin" size 12432672 crc ad711555 md5 3cd6fa12c89378065155062be78b4251 sha1 930bb2d22b555c177d3d5271d83f16b35aa8f42f )
	rom ( name "After Burner III (Japan) (Track 04).bin" size 5769456 crc 3f5003b1 md5 0b2a9b2817a84eb269021f565234407c sha1 8051ee6fd332ecf2e6224c34da0952df19ebb51f )
	rom ( name "After Burner III (Japan) (Track 05).bin" size 14558880 crc ab5794c3 md5 046c9f072bf36c7cc12c43acd5b26a39 sha1 6ad36d49eb12eb4321e5ae2cf4f7db56b61d4cf0 )
	rom ( name "After Burner III (Japan) (Track 06).bin" size 58371936 crc 86a30f77 md5 970dd1248f45a97c366a56efad297e3c sha1 b7800397c4bc9436e2b2e8a5c249d57f5da3b93c )
	rom ( name "After Burner III (Japan) (Track 07).bin" size 57972096 crc cea674df md5 504576a9dc1ff37b8cdb20ebc315b667 sha1 a415e051c2c76d86921b2e87cd7ba1a2d232cd1b )
	rom ( name "After Burner III (Japan) (Track 08).bin" size 60902688 crc 88ee1bfb md5 1cc6b56cdb70dc6406880fabde7aff49 sha1 8e8ac8abc085ec6dcc701e5af331a864150d9da0 )
	rom ( name "After Burner III (Japan) (Track 09).bin" size 52277904 crc 37441bd9 md5 6c9bd1d6aaff69398fbe662e756fbe12 sha1 2a0c1f931993c90e5ac90e23a46f3c5a3b45993f )
	rom ( name "After Burner III (Japan) (Track 10).bin" size 54199488 crc b522e646 md5 6b42b2346e04f5d5148e750bb4e82885 sha1 e695fe634bb74e593f20a8500b108f067494cbd1 )
	rom ( name "After Burner III (Japan) (Track 11).bin" size 56189280 crc 5e9e6657 md5 b29513a6cd59f6a59a3d96236a54aac4 sha1 86f15ab0fb6b72eefe30d4de9daafd0d5dca1d48 )
	rom ( name "After Burner III (Japan) (Track 12).bin" size 59724336 crc a4b53073 md5 c935c273d48bc74e6e75a831e6072f8b sha1 ce8c6b93323f7b83c8ef3be8260efee07533955a )
)

game (
	name "AH3 - ThunderStrike (USA)"
	description "AH3 - ThunderStrike (USA)"
	rom ( name "AH3 - ThunderStrike (USA).cue" size 1422 crc d83f8b35 md5 2ad3ed787212a34ca647f5484fb44beb sha1 c7ef1d64d8f57bbe6e2de6d618d070469d78ba8e )
	rom ( name "AH3 - ThunderStrike (USA) (Track 01).bin" size 147500976 crc 6ea8ee5b md5 76066ebf8ee7abe3ea24fb96e9ddda22 sha1 7e5f1293f8c35d4e76e7a7767f438278744e4b09 )
	rom ( name "AH3 - ThunderStrike (USA) (Track 02).bin" size 38704512 crc 3574a538 md5 e827b706a28e39edf7fed17eade91bd8 sha1 5f8b4c969b7f1d0035c70a6abee468e14cbe825f )
	rom ( name "AH3 - ThunderStrike (USA) (Track 03).bin" size 38532816 crc 24f7892a md5 878a89bcd1e5c246e1be9614ba6958d5 sha1 6528f5ba7d78cd434b5841a18976ecb9078b2420 )
	rom ( name "AH3 - ThunderStrike (USA) (Track 04).bin" size 15692544 crc 9fbde617 md5 216c3651e969cf52982fb566f2cd76b7 sha1 f0f99174e3d7ae6ff304e4ce456dd28ff5309253 )
	rom ( name "AH3 - ThunderStrike (USA) (Track 05).bin" size 10094784 crc 5b9d35e1 md5 0042b7f52a25d287e21a2602cdb659b4 sha1 ea75da75a7c527171e8fb1ffafc39485139eda9c )
	rom ( name "AH3 - ThunderStrike (USA) (Track 06).bin" size 20039040 crc 080c09a3 md5 f3f297bb9ab51ec6a25399f56ee13610 sha1 ac72712924e33e91cc9c4eda2d2748602db5139d )
	rom ( name "AH3 - ThunderStrike (USA) (Track 07).bin" size 40656672 crc d25e5922 md5 d985b3ebef4458765cf789c83c0f9696 sha1 48b7a8df8b2548385ca71e87707f506b42e2029b )
	rom ( name "AH3 - ThunderStrike (USA) (Track 08).bin" size 40717824 crc 6394f6d3 md5 98c208cb334dff4095000c8ef121b75e sha1 75303b0ce91bfa64df92b9f5bbdf3dc999bf76db )
	rom ( name "AH3 - ThunderStrike (USA) (Track 09).bin" size 25077024 crc 779b8485 md5 fce5bdbe107cac9e7e30d30ce0d0bac6 sha1 46258c7a1b1dfdde7bed4a97de70995039386a35 )
	rom ( name "AH3 - ThunderStrike (USA) (Track 10).bin" size 44248176 crc 627a5436 md5 4c437b6489872f64a1d20c3a165834ed sha1 7e018dd3451ce1cdc7479262ffb9730cca5281ac )
	rom ( name "AH3 - ThunderStrike (USA) (Track 11).bin" size 52941168 crc 366fd589 md5 3fa41927d94fced8cbfec6990ad30de8 sha1 e7175bf2b561574877ef37011a04be021e80ed19 )
	rom ( name "AH3 - ThunderStrike (USA) (Track 12).bin" size 1907472 crc cda28c20 md5 53370c3315e0e999e3e8da018e631c4a sha1 947b9923f4483eecda255fc85f48bb7e9c280a72 )
)

game (
	name "AX-101 (Japan)"
	description "AX-101 (Japan)"
	rom ( name "AX-101 (Japan).cue" size 198 crc 6c514d73 md5 1b4d05efd8ec782a3630577631130efe sha1 7c84137a2d805a8d764ca868172ecdd3f753db73 )
	rom ( name "AX-101 (Japan) (Track 1).bin" size 615817104 crc 03cbf674 md5 cb1e01076185d819f0bec8350fc1744b sha1 616da93bfe4c511dcab19bbbf3aebcac4876a2ee )
	rom ( name "AX-101 (Japan) (Track 2).bin" size 2352000 crc 3fd8d737 md5 2fa70fa9851d5acc23a40274307e8313 sha1 4a9c6a396cd5e71e79577771b0b096ba7e6366e9 )
)

game (
	name "Bari-Arm (Japan)"
	description "Bari-Arm (Japan)"
	rom ( name "Bari-Arm (Japan).cue" size 2091 crc 03cc6d8a md5 1642a20b0a1f286f1759c484e17adbed sha1 c75655c9d99aaf893913137cd6a7a255fb7ede6a )
	rom ( name "Bari-Arm (Japan) (Track 01).bin" size 16849728 crc af764474 md5 b085a96a1f51fd4f29900af0bd1f86fd sha1 805003e27212c103478fe3d04ef28c794712394e )
	rom ( name "Bari-Arm (Japan) (Track 02).bin" size 22042944 crc 0b7d7a8e md5 571da46d33c9c201e08e0437228c5125 sha1 a052069c7a74e1cc6ecb214254e629302f777354 )
	rom ( name "Bari-Arm (Japan) (Track 03).bin" size 21419664 crc 584abbfe md5 a59881a5644bc67f066eff0e1de87959 sha1 37a5bf6e0c39aee8c9bd7a9825516a6e1cdef169 )
	rom ( name "Bari-Arm (Japan) (Track 04).bin" size 8344896 crc 6c5421fc md5 c54e640ceab83cbe93b0617422f509ac sha1 31677076ffe32c654135b4d1d64edbb8ff74dcb3 )
	rom ( name "Bari-Arm (Japan) (Track 05).bin" size 32937408 crc 47acefb4 md5 cf2a74193f0ed7e6e5fc4a0633fbc68f sha1 2585467855a9c53504123253fe7723dc231252e0 )
	rom ( name "Bari-Arm (Japan) (Track 06).bin" size 7909776 crc 53bbe4c6 md5 5d5a37948867cbaa283aecbc0cff5d34 sha1 d334f2403e29838cc37002fca5ea836be9eacfe3 )
	rom ( name "Bari-Arm (Japan) (Track 07).bin" size 32189472 crc 4af2b56c md5 c05680168a6e13134e4148b3caf27a74 sha1 26340b300c49978b7d7d07a1f08a2cf93aeba9e3 )
	rom ( name "Bari-Arm (Japan) (Track 08).bin" size 2224992 crc 7ba7a6cc md5 50053abfd2d7f33cb0c7a3b51f4821f3 sha1 59ec15d37068ae5b95eb3d525225abb927206a31 )
	rom ( name "Bari-Arm (Japan) (Track 09).bin" size 29976240 crc 527b54fe md5 6066b8c9a0c593e30b6e9234dc39ac40 sha1 7c72e0ff1eaf84eb0f5415ffaa46313fc555d2eb )
	rom ( name "Bari-Arm (Japan) (Track 10).bin" size 19453392 crc f7643dec md5 9030c54422542178447d18278edbfdec sha1 b56abeebbe192c38a56b1be1ea487729555adb4e )
	rom ( name "Bari-Arm (Japan) (Track 11).bin" size 20855184 crc bc57a263 md5 1ce6672ff90b28e3f640d2ad8cadbf20 sha1 5725a07a81defa1a7338d5f1d0cf9eb8e66fdeee )
	rom ( name "Bari-Arm (Japan) (Track 12).bin" size 32516400 crc 61693654 md5 efbe3fb616ccfe89a8a369bfddcb2d71 sha1 7c7107753b087f5443b99bd6a20ed058c7931d00 )
	rom ( name "Bari-Arm (Japan) (Track 13).bin" size 5214384 crc 4e4bee6c md5 02563defb6afaed928c08cb0866d1a0d sha1 4bef208d82b2af1a5d588139a00ed5a5938ecf89 )
	rom ( name "Bari-Arm (Japan) (Track 14).bin" size 32238864 crc 64d4f9fa md5 bda7810b95e0c2106d5a17d04a2c6cf3 sha1 387d8be7414561144892ef7b77241e8b26008310 )
	rom ( name "Bari-Arm (Japan) (Track 15).bin" size 21798336 crc 7aad0b67 md5 8d5fcf32048d97bb323b109fbf8d2f41 sha1 ef464d390f889db3e84021f7976422b7c3ff15ff )
	rom ( name "Bari-Arm (Japan) (Track 16).bin" size 21024528 crc 13b59cf8 md5 2897c0572430a1b7c88dc0c13e425995 sha1 be30e5346bf87e0680400d8defa127f0841f64e3 )
	rom ( name "Bari-Arm (Japan) (Track 17).bin" size 22285200 crc 67d02acc md5 16e5228e30611b28e17f8b7a42a829a5 sha1 52aaa0a8c71470b81dce0e510868a76522ced47b )
	rom ( name "Bari-Arm (Japan) (Track 18).bin" size 11802336 crc 46da7909 md5 9c25604546319a6c9b3336fa9f95a8da sha1 6cef2fd84bf3d6ec3861e37fa0ca265b6ad5a2d5 )
	rom ( name "Bari-Arm (Japan) (Track 19).bin" size 1505280 crc f68eb74b md5 2733c83e16e0004e4873907e8845dd50 sha1 245690c9b2c811dd83cabeb5460630da22e31d20 )
)

etc.
```

I want to filter out all entries that do not match (USA).  So, everything that says (Japan) would disappear.  How would I parse that line and delete everything under the game "paragraph"?  Additionally, it says 111 in the description, which is the number of "paragraphs" in the file, how would I update that?

---

### Post by Liolikas on 2009-09-25
Learn AWK and grep tools (commands).

---

### Post by NoaHall on 2009-09-25
cat NAMEOFFILE | grep USA 

Note, grep is case sensitive.

---

### Post by Liolikas on 2009-09-25
Everything in Linux is case sensitive. <snip>

---

### Post by NoaHall on 2009-09-25
I was saying it to be helpful. There was no need for you to say that.

---

### Post by Liolikas on 2009-09-25
ty now try:
cat NAMEOFFILE | grep [Uu][Ss][Aa] 
;)

---

### Post by NoaHall on 2009-09-25
Why? That's a waste of time. The "USA" is in capitals only. He doesn't need it in lower case.

---

### Post by Elfo33 on 2009-09-25
Thank you Noahall, that is quite helpful.  Grep looks very powerful from the quick wiki entries I just read, but what does "cat" do?

---

### Post by NoaHall on 2009-09-25
cat displays the content of a file in the terminal.

So if I had a file which had "hello, you" in it, it would be 

```
cat /home/noah/hellofile

hello, you
```

---

### Post by bapoumba on 2009-09-25
Subscribing, just because.

---

