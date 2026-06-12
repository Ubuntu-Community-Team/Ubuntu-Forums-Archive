---
title: "Xfire thru Wine almost working.  Need Help"
date: 2006-02-25
forum: General Help
---

### Post by HIGHLIFE on 2006-02-25
Ok so I installed Xfire and registered the Mozilla Control .dll but when I Login it comes up with:

The Xfire Service had encountered a problem in the following application:
C:\Program Files\Xfire\Xfire.exe

and then gives a big long error report to upload to Xifre.

Could some one please help fix it so it doesnt come up with this report.:confused: 

thx in advance

---

### Post by HIGHLIFE on 2006-02-25
No one?

---

### Post by R3linquish3r on 2006-03-04
I got this error too. If anyone needs to see the error to have an idea of whats goin on here it is:

```
<?xml version="1.0" encoding="utf-8" ?>

<ExceptionReport Version="4">
	<Application Build="17902" Command="&quot;C:\Program Files\Xfire\Xfire.exe&quot;"/>
	<OperatingSystem Type="2"><Version Major="5" Minor="0" Build="2195"/></OperatingSystem>
	<Exception Code="C0000005" Address="B7EDBC00"></Exception>
	<Registers EAX="7D1C0EC8" EBX="7C50DAF4" ECX="7D1C0EC7" EDX="00000000" ESI="7D1C0EC8" EDI="7D1C0EA0" CS="0073" EIP="B7EDBC00" SS="007B" ESP="7FB0DFBC" EBP="7FB0DFC0" DS="007B" ES="007B" FS="1007" GS="0033" Flags="00210202"/>
	<BackTrace>
		<Frame ProgramCounter="B7EDBC00" StackAddress="7FB0DFBC" FrameAddress="7FB0DFC0">
			<StackHexDump From="7FB0DFBC" To="7FB0DFC0">00 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7C4C435D" StackAddress="7FB0DFC8" FrameAddress="7FB0E200">
			<Module Section="0001" Offset="0002335D" FileName="c:\windows\system32\wined3d.dll"/>
			<StackHexDump From="7FB0DFC0" To="7FB0E040">00 e2 b0 7f	5d 43 4c 7c	c8 0e 1c 7d	00 00 00 00	00 e2 b0 7f	19 43 4c 7c	a0 9a 9d 7f	20 63 d7 7f	a0 9a 9d 7f	ae db ea 7b	a0 9a 9d 7f	ff ff 00 00	20 e0 b0 7f	fc 25 d1 7f	a0 9a 9d 7f	ff ff 00 00	30 e0 b0 7f	34 9b eb 7b	60 e0 b0 7f	00 00 d7 7f	00 00 d7 7f	ea d5 ea 7b	20 00 d7 7f	fc 34 ef 7b	70 e0 b0 7f	0f a8 eb 7b	20 00 d7 7f	50 01 00 00	70 e0 b0 7f	1e a7 eb 7b	a0 9a 9d 7f	4c 03 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7C4C6EE0" StackAddress="7FB0E208" FrameAddress="7FB0E250">
			<Module Section="0001" Offset="00025EE0" FileName="c:\windows\system32\wined3d.dll"/>
			<StackHexDump From="7FB0E200" To="7FB0E250">50 e2 b0 7f	e0 6e 4c 7c	00 00 19 7d	a8 11 1c 7d	30 e2 b0 7f	ea d5 ea 7b	20 00 d7 7f	10 85 25 7d	70 e2 b0 7f	0f a8 eb 7b	20 00 d7 7f	00 00 00 00	10 01 00 00	00 01 00 00	40 dc 15 7d	ea d5 ea 7b	20 00 d7 7f	b8 b6 15 7d	b0 11 1c 7d	00 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7D1553E4" StackAddress="7FB0E258" FrameAddress="7FB0E2E0">
			<Module Section="0001" Offset="000143E4" FileName="c:\windows\system32\d3d8.dll"/>
			<StackHexDump From="7FB0E250" To="7FB0E2D0">e0 e2 b0 7f	e4 53 15 7d	a0 0e 1c 7d	00 00 00 00	01 00 00 00	44 00 03 00	20 00 00 00	9c e2 b0 7f	b8 11 1c 7d	b0 11 1c 7d	00 4d 15 7d	08 00 00 00	10 01 00 00	c0 c2 50 7c	00 00 19 7d	f4 da 50 7c	20 00 00 00	00 05 00 00	00 04 00 00	10 e3 b0 7f	14 e3 b0 7f	18 e3 b0 7f	1c e3 b0 7f	20 e3 b0 7f	00 00 00 00	24 e3 b0 7f	28 e3 b0 7f	2c e3 b0 7f	30 e3 b0 7f	34 e3 b0 7f	38 e3 b0 7f	3c e3 b0 7f</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7D9160AC" StackAddress="7FB0E2E8" FrameAddress="7FB0E3D0">
			<Module Section="0001" Offset="000050AC" FileName="C:\Program Files\Xfire\xfire_toucan_17902.dll"/>
			<StackHexDump From="7FB0E2E0" To="7FB0E360">d0 e3 b0 7f	ac 60 91 7d	98 20 21 7d	00 00 00 00	01 00 00 00	44 00 03 00	20 00 00 00	10 e3 b0 7f	ac e3 b0 7f	a8 dc dc 7f	00 00 00 00	00 00 16 7d	00 00 00 00	00 00 00 00	16 00 00 00	01 00 00 00	00 00 00 00	01 00 00 00	44 00 03 00	01 00 00 00	00 00 00 00	50 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 05 00 00	00 04 00 00	3c 00 00 00	16 00 00 00	20 00 00 00	f3 63 91 7d	00 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7D92DE3F" StackAddress="7FB0E3D8" FrameAddress="7FB0E3E4">
			<Module Section="0001" Offset="0001CE3F" FileName="C:\Program Files\Xfire\xfire_toucan_17902.dll"/>
			<StackHexDump From="7FB0E3D0" To="7FB0E3E4">e4 e3 b0 7f	3f de 92 7d	e8 94 96 7d	e8 94 96 7d	34 e7 dc 7f</StackHexDump>
		</Frame>
		<Frame ProgramCounter="004F2989" StackAddress="7FB0E3EC" FrameAddress="7FB0E3F0">
			<Module Section="0001" Offset="000F1989" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="7FB0E3E4" To="7FB0E3F0">f0 e3 b0 7f	89 29 4f 00	01 9a 9d 7f</StackHexDump>
		</Frame>
		<Frame ProgramCounter="0042537B" StackAddress="7FB0E3F8" FrameAddress="7FB0E688">
			<Module Section="0001" Offset="0002437B" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="7FB0E3F0" To="7FB0E470">88 e6 b0 7f	7b 53 42 00	01 9a 9d 7f	a8 dc dc 7f	c8 c5 df 7f	a8 dc dc 7f	01 9a 9d 7f	ff ff 00 00	40 e4 b0 7f	8c 36 cf 7f	a0 9a 9d 7f	a0 9a 9d 7f	a0 9a 9d 7f	ee 35 cf 7f	a0 9a 9d 7f	ff ff 00 00	cc 40 ec 7f	ea d5 ea 7b	ed dd c9 7f	fc 25 d1 7f	70 e4 b0 7f	ae db ea 7b	a0 9a 9d 7f	a0 9a 9d 7f	cc 40 ec 7f	fc 25 d1 7f	a0 9a 9d 7f	4a 4f 00 00	90 e4 b0 7f	ea d5 ea 7b	ed dd c9 7f	fc 25 d1 7f</StackHexDump>
		</Frame>
		<Frame ProgramCounter="00423D7C" StackAddress="7FB0E690" FrameAddress="7FB0E6C4">
			<Module Section="0001" Offset="00022D7C" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="7FB0E688" To="7FB0E6C4">c4 e6 b0 7f	7c 3d 42 00	a8 dc dc 7f	a8 dc dc 7f	e8 ee b0 7f	a8 dc dc 7f	a8 dc dc 7f	bc e6 b0 7f	d4 e6 b0 7f	c0 e6 b0 7f	c0 e6 b0 7f	79 57 40 00	00 00 00 00	a8 dc dc 7f	00 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="004240AC" StackAddress="7FB0E6CC" FrameAddress="7FB0E6F4">
			<Module Section="0001" Offset="000230AC" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="7FB0E6C4" To="7FB0E6F4">f4 e6 b0 7f	ac 40 42 00	a8 dc dc 7f	cc ee b0 7f	00 00 00 00	00 00 21 7d	4c 02 00 00	15 00 00 00	00 00 00 00	00 00 00 00	07 00 00 00	00 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="0042B9A6" StackAddress="7FB0E6FC" FrameAddress="7FB0EF34">
			<Module Section="0001" Offset="0002A9A6" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="7FB0E6F4" To="7FB0E774">34 ef b0 7f	a6 b9 42 00	a8 dc dc 7f	20 4e e0 7f	01 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	dd 43 8e 7e	ec db 93 7e	5c e7 b0 7f	a5 f3 8e 7e	e0 08 94 7e	01 00 00 00	5c e7 b0 7f	87 f3 8e 7e	4f e3 17 7f	ff ff 00 00	a0 9a 9d 7f	a0 9a 9d 7f	c0 0b 9d 7f	08 0b e0 7f	06 00 00 00	64 b6 e7 7e	4a 00 02 00	01 00 00 00	7c e7 b0 7f	d8 95 e3 7e	4a 00 02 00	4c 03 00 00	01 00 00 00	a0 9a 9d 7f</StackHexDump>
		</Frame>
		<Frame ProgramCounter="00427424" StackAddress="7FB0EF3C" FrameAddress="7FB0EF78">
			<Module Section="0001" Offset="00026424" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="7FB0EF34" To="7FB0EF78">78 ef b0 7f	24 74 42 00	a8 dc dc 7f	20 4e e0 7f	10 e3 dc 7f	00 00 01 00	00 07 00 00	97 2b 43 00	00 00 01 00	d8 28 e0 7f	60 ef b0 7f	00 00 00 00	00 00 01 00	88 72 e0 7f	00 00 00 00	ab 07 00 00	00 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="004E0586" StackAddress="7FB0EF80" FrameAddress="7FB0EFA4">
			<Module Section="0001" Offset="000DF586" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="7FB0EF78" To="7FB0EFA4">a4 ef b0 7f	86 05 4e 00	d8 28 e0 7f	d8 28 e0 7f	ab 07 00 00	71 7d 4d 00	01 00 00 00	d8 28 e0 7f	00 00 00 00	00 00 00 00	00 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="004CD1C6" StackAddress="7FB0EFAC" FrameAddress="7FB0EFBC">
			<Module Section="0001" Offset="000CC1C6" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="7FB0EFA4" To="7FB0EFBC">bc ef b0 7f	c6 d1 4c 00	64 b6 e7 7e	30 f6 b0 7f	24 00 01 00	00 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7EE5A34A" StackAddress="7FB0EFC4" FrameAddress="7FB0EFEC">
			<Module Section="0001" Offset="0009934A" FileName="c:\windows\system32\user32.dll"/>
			<StackHexDump From="7FB0EFBC" To="7FB0EFEC">ec ef b0 7f	4a a3 e5 7e	24 00 01 00	00 80 00 00	0c 01 00 00	01 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	64 b6 e7 7e	24 00 01 00	30 f6 b0 7f</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7EE5AF96" StackAddress="7FB0EFF4" FrameAddress="7FB0F02C">
			<Module Section="0001" Offset="00099F96" FileName="c:\windows\system32\user32.dll"/>
			<StackHexDump From="7FB0EFEC" To="7FB0F02C">2c f0 b0 7f	96 af e5 7e	cb d0 4c 00	24 00 01 00	00 80 00 00	0c 01 00 00	01 00 00 00	64 b6 e7 7e	2c f0 b0 7f	42 af e5 7e	eb 7e b0 7f	00 80 00 00	cb d0 4c 00	64 b6 e7 7e	0c 01 00 00	30 f6 b0 7f</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7EE60341" StackAddress="7FB0F034" FrameAddress="7FB0F4DC">
			<Module Section="0001" Offset="0009F341" FileName="c:\windows\system32\user32.dll"/>
			<StackHexDump From="7FB0F02C" To="7FB0F0AC">dc f4 b0 7f	41 03 e6 7e	0c 01 00 00	01 00 00 00	dc f4 b0 7f	46 02 e6 7e	02 00 00 00	60 f0 b0 7f	00 00 00 00	01 00 00 00	00 00 00 00	c1 20 92 7d	60 f0 b0 7f	00 00 00 00	00 00 00 00	10 f4 b0 7f	cb d0 4c 00	03 1e e1 7e	00 00 00 00	01 00 00 00	10 f4 b0 7f	00 20 92 7d	40 00 00 00	50 f1 b0 7f	ae db ea 7b	00 00 00 00	00 00 00 00	03 00 00 00	9f 20 92 7d	00 00 00 00	00 00 00 00	00 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7EE2D592" StackAddress="7FB0F4E4" FrameAddress="7FB0F51C">
			<Module Section="0001" Offset="0006C592" FileName="c:\windows\system32\user32.dll"/>
			<StackHexDump From="7FB0F4DC" To="7FB0F51C">1c f5 b0 7f	92 d5 e2 7e	f4 ab eb 7e	24 00 01 00	00 80 00 00	0c 01 00 00	01 00 00 00	64 b6 e7 7e	1c f5 b0 7f	5b d5 e2 7e	48 37 41 00	f4 ab eb 7e	00 00 00 00	00 00 00 00	00 00 00 00	30 dc dc 7f</StackHexDump>
		</Frame>
		<Frame ProgramCounter="00420D6F" StackAddress="7FB0F524" FrameAddress="7FB0F9F4">
			<Module Section="0001" Offset="0001FD6F" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="7FB0F51C" To="7FB0F59C">f4 f9 b0 7f	6f 0d 42 00	30 f6 b0 7f	14 fa b0 7f	00 00 59 7d	00 00 00 00	00 00 00 00	00 00 00 00	d4 0b 00 00	49 00 00 00	f8 00 00 00	9d 00 00 00	12 01 00 00	35 00 32 00	35 00 78 00	33 00 36 00	34 00 00 00	00 00 d7 7f	e8 ec df 7f	70 00 00 00	00 00 d7 7f	00 ed df 7f	00 00 00 00	60 00 00 00	fc 34 ef 7b	00 00 d7 7f	d8 ec df 7f	00 00 6f 00	62 00 69 00	61 00 73 00	00 00 ef 7b	00 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="0041D5DB" StackAddress="7FB0F9FC" FrameAddress="7FB0FEA8">
			<Module Section="0001" Offset="0001C5DB" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="7FB0F9F4" To="7FB0FA74">a8 fe b0 7f	db d5 41 00	a8 dc dc 7f	08 ff b0 7f	44 8f 44 00	90 db dc 7f	08 00 00 00	ff 00 00 00	88 00 00 00	01 00 00 00	a8 dc dc 7f	00 00 00 00	40 fa b0 7f	00 fc b0 7f	5c fa b0 7f	90 fa b0 7f	40 00 00 00	30 fb b0 7f	28 00 00 00	34 00 00 c0	00 00 00 00	ff ff ff ff	ce a6 ee 7f	00 00 00 00	00 00 00 00	00 00 00 00	9c fa b0 7f	64 b6 e7 7e	90 fa b0 7f	d0 fa b0 7f	0c fb b0 7f	58 bd e3 7e</StackHexDump>
		</Frame>
		<Frame ProgramCounter="00448F96" StackAddress="7FB0FEB0" FrameAddress="7FB0FF08">
			<Module Section="0001" Offset="00047F96" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="7FB0FEA8" To="7FB0FF08">08 ff b0 7f	96 8f 44 00	90 db dc 7f	0a 00 00 00	e0 f1 ef 7b	44 8f 44 00	fc 25 d1 7f	44 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	01 00 00 00	00 00 00 00	0c 00 00 00	10 00 00 00	14 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7FCDDC9F" StackAddress="7FB0FF10" FrameAddress="7FB0FFE8">
			<Module Section="0001" Offset="0004CC9F" FileName="c:\windows\system32\kernel32.dll"/>
			<StackHexDump From="7FB0FF08" To="7FB0FF88">e8 ff b0 7f	9f dc cd 7f	e0 f1 ef 7b	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	ff ff ff ff	f8 df c9 7f	10 29 cb 7f	fc 25 d1 7f	00 00 11 00	00 40 ec 7f	e8 ff b0 7f	10 ff b0 7f	33 dc cd 7f	01 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00</StackHexDump>
		</Frame>
	</BackTrace>
</ExceptionReport>

```

If anyone could come up with a solution it would be awesome.

---

### Post by Dylan103 on 2006-03-04
Try changing it to load from the acutal file directory, cause its tyring to load like a windows program like C:/Program Files/Xfire/xfire.exe
so I havn't had xfire on linux, but maybe like /etc/xfire/xfire.(w/e the filetype is)

---

### Post by R3linquish3r on 2006-03-05
Thats were the Program Files is. I'm using Wine and its in the fake C Drive. The program runs I just get that error when I try to login.

---

### Post by fuzzypig on 2007-06-03
OMFG

lol, this is what happened:

[IMG]http://img03.picoodle.com/img/img03/8/6/3/f_Screenshotxm_c578852.png[/IMG]

---

