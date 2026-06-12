---
title: "can someone tell me how i can view the contents of a .exe file ?"
date: 2010-09-02
forum: General Help
---

### Post by nagaprathyush on 2010-09-02
Hiii, my name is NagaPrathyush. Am new to these forums and greetings everyone. 
Coming to the main topic, I know linux ubuntu 10.04 cannot open a .exe file but what am asking is for a program or application to view what code is written inside a .exe file. The issue came up when I inserted a usb into my laptop and found the contents of autorun.inf file as 

[autorun]
open=Recycle\X-5-4-27-2345678318-4567890223-4234567884-2341\RisinG.exe
icon=%SystemRoot%\system32\SHELL32.dll,4
action=Open folder to view files
shell\open=Open
shell\open\command=Recycle\X-5-4-27-2345678318-4567890223-4234567884-2341\RisinG.exe
shell\open\default=1

I remember having seen the RECYCLER folder before but not the "Recycle" one. I was pretty sure it was a virus or worm or something malicious at the least. As said above in the script, I understood that the script was made to run the rising.exe file on a winows machine. Thank god, am saved (god bless Linux;)).....but on the other hand, I was curious as of what the .exe file was made to do. Can someone suggest me a program to view the .exe files contents ?

Cheers & thanks, in advance!
NagaPrathyush(You can call me Naga ):P)

---

### Post by MooPi on 2010-09-02
Don't know if this will help but I just viewed an .exe with xedit . xedit comes with all Ubuntu installs and can be started by terminal or ctrl + F2

---

### Post by Silent Warrior on 2010-09-02
I don't know much about programming, but I think all you can see by opening the file is op-code (assembly?). To see the actual code... well, you'd need the actual code. Maybe a debugger could help you along? I suppose that approach would have to work through Windows/Wine.
Those lines actually don't look malicious to me, though I'm no expert. You could set the .exe-file to be executable - it sounds like you didn't do that yet.
... Uh, hey, what's RisinG, anyway? Some kind of game? Maybe you should look into that before doing anything else. I'll just... excuse myself due to not knowing anything of use. :oops:

---

### Post by endotherm on 2010-09-02
I usually use strings.exe from the sysinternals suite to read whatever text is in it, and use dumpBin from the visual studio tools for reading the metadata associated. 
other than that, there isn;t much you can do to get into it other than disassembling/decompiling it, unless it uses an interpretive runtime. if it uses java or .net you can at least disassemble to MSIL/CLR or to JVM assembler. there are also some high level decompilers for jars and .net exes.

---

### Post by Mark Phelps on 2010-09-02
> **nagaprathyush said:**
> Hiii, my name is NagaPrathyush. Am new to these forums and greetings everyone. 
Coming to the main topic, I know linux ubuntu 10.04 cannot open a .exe file but what am asking is for a program or application to view what code is written inside a .exe file.

If the .exe file was built from a 3rd-gen programming language, it does not actually contain the source code; instead, it contains object code processed through a linkage editor to turn it into executable code.  

Some language editors can represent the code as a form of pseudo-assembler code.

To actually see the source, you would have to go through a process known as disassembling -- and even then, you won't see the actual "english" version of the source code, you will only see what the disassembler is able to generate.

---

### Post by limestone on 2010-09-02
.exe is a binary file containing binary code which you can't read anyway...
So you'll need the source-code

You could use a reverse engineering program to get the binary to readable code but that would take forever 
if it's even possible..

---

### Post by gypsumwolf on 2010-09-02
You could try using [http://www.angusj.com/resourcehacker/]("http://www.angusj.com/resourcehacker/")

I have not tried to run it under wine, but it probably will work just fine.

---

### Post by endotherm on 2010-09-02
> **pont.andersson said:**
> .exe is a binary file containing binary code which you can't read anyway...
So you'll need the source-code

You could use a reverse engineering program to get the binary to readable code but that would take forever 
if it's even possible..
that is largely true, but there is still a lot of information you can pull out of an exe, including every string embedded in it, as strings don't get compiled, but just en/decoded against ASCII/EBCDIC/unicode. all the header infomation in the file is also visible. there is also the question of whether the code is binary compiled or interpreted (.net code renders a PE exe, but the code is not binary compiled, but instead jit'ed against the runtime line by line). in these cases it is very easy to analyze the code with tools like disasm. I;ve used java and python decompilers as well in times past (not disassemblers, but full decompilers that render java code, but with generic variable names). also if you can get debug symbols for the code, you can gain a great deal of insight into the code, and can sometimes decompile back to the original code with var names intact.

a C compiled executable however is just as you state; all you can get out of it are  strings and headers unless you disassemble.

---

### Post by lisati on 2010-09-02
I'd suggest using the "strings" command as a starting place. 

Like others have said, the contents of ".EXE" and ".DLL" files (and similar) are in a form better suited for "reading" by a computer than by a human. Full reverse engineering of the contents of the file (which might not always be appreciated by the original supplier of the file) is beyond the scope of a short answer like this one.

---

### Post by coolman98 on 2010-09-02
use assembler and attach to proscess for assembly code.

---

### Post by nagaprathyush on 2010-09-03
yeah, well I was too scared to run the rising.exe file on my windows (after noticing it on my ubuntu).... so I was just looking to find out what it is all about  I mean trying to find out what it does if its run, without actually running it :D Its a long road ahead, I suppose.... Thanks for the whole lotta replies! This certainly is a vibrant community ;)

Regards

---

### Post by limestone on 2010-09-03
You could run it in a virtual box windows and see what happens
[URL="http://ubuntuforums.org/showthread.php?t=1566396"]
[/URL]

---

### Post by 3rdalbum on 2010-09-03
[http://www.greatis.com/appdata/d/r/rising.exe.htm](http://www.greatis.com/appdata/d/r/rising.exe.htm)

That's what it does.

---

### Post by nagaprathyush on 2010-09-04
upon strings command..... "strings RisinG.exe "

h;zr
nxr&nxrsnxr?|xr
vr$Fxr
Stub
VB5!6&*
Stub
Stub
Stub
mMain
CCrypto
Module1
Stub
LockResource
kernel32
FindResourceA
LoadResource
SizeofResource
FreeResource
GetModuleHandleA
user32
SetTimer
RtlMoveMemory
GetProcAddress
hH @
CreateProcessA
CallWindowProcA
LoadLibraryA
h$!@
WriteProcessMemory
hp!@
Class
C:\Windows\system32\MSVBVM60.DLL\3
VBRUN
Sleep
advapi32.dll
CryptAcquireContextA
hD#@
CryptCreateHash
CryptDeriveKey
CryptDestroyHash
h $@
CryptDestroyKey
hh$@
CryptEncrypt
CryptDecrypt
CryptHashData
hD%@
CryptReleaseContext
Encrypt
Decrypt
VBA6.DLL
sTextToEncrypt
sPrivateKey
bReturnTextInHex
enEncryptionType
sTextToDecrypt
bTextSuppliedInHex
MSVBVM60.DLL
MethCallEngine
EVENT_SINK_AddRef
DllFunctionCall
EVENT_SINK_Release
EVENT_SINK_QueryInterface
__vbaExceptHandler
ProcCallEngine
wIez
`SXcF
}*+L
+ZlN
 and more of unreadable text..........
I take it that it that the strings command just picked up all the alphabets from ,exe file :D Thanks for the confirmation, Mr.3rdalbum .....I can see things clearly now ;)

---

