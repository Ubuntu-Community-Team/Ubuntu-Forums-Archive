---
title: "Wine DCOM98 error :("
date: 2005-03-16
forum: General Help
---

### Post by canglan on 2005-03-16
Hello,

I have installed wine winetools libwine via apt-get. After I run wintools in terminal, I have created the fake windows partition as step 1. However, the next bit isn't successful. Once I tried to install DCOM98, it prompts the following error message:

Exception raised
Unhandled page fault on read access to 0x00000010 at address 0x010058f6.
Do you wish to debug it?

Could anyone kindly help me out? :(

Thanks in advance!

---

### Post by canglan on 2005-03-16
If I choose to debug it, there prompts the following error:

Error registering the OCX c:\windows\system\ole32.dll

---

### Post by StacyWebb on 2005-03-16
Try installing DCOM95 instead of 98. This should run all the windows specific apps your trying to install.

---

### Post by canglan on 2005-03-16
Emmm, it's really strange, somehow it works now. I tried to install DCOM95 on win95, then changed back to win98 and installed DCOM98... :/

---

### Post by canglan on 2005-03-16
Now, Internet Explorer isn't installing properly. :(
The setup window and process seems okay, but it then tells me the installation is failed.

Any idea?

---

### Post by canglan on 2005-03-16
Here's the error message I get from terminal:


err:ver:GetFileVersionInfoW Cannot access NE resource in L"C:\\windows\\msdownld.tmp\\AS0078B4.tmp\\w95inf16.dll"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\msdownld.tmp\\AS0078B4.tmp\\w95inf16.dll" -> "c:\\windows\\system\\w95inf16.dll"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\msdownld.tmp\\AS0078B4.tmp\\w95inf32.dll" -> "c:\\windows\\system\\w95inf32.dll"
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\system\\autokill.inf"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\system\\autokill.exe"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\system\\ie4olrdr.map"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\advpack.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Bindlist.txt"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Softboot.txt"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Bindlist.log"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\Softboot.log"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\ierunonce.log"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\ierunonce.err"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\system\\npstub.dll"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Web\\egg.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Web\\dskwmark.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Web\\tck.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Web\\wmark.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Web\\userexbg.gif"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Web\\userexp.htm"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Web\\compon.htm"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "c:\\windows\\Web\\desktop.htx"
err:setupapi:SetupDefaultQueueCallbackA delete error 3 "C:\\PROG~FBU\\setup\\ie4.inf"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "C:\\PROG~FBU\\ie40.cif"
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "C:\\PROG~FBU\\ie4.txt"
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "c:\\windows\\inf\\ie5dom.inf"
fixme:crypt:CryptRegisterDefaultOIDFunction (1,CertDllVerifyRevocation,0,L"mscrlrev.dll") stub!
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
err:setupapi:SetupDefaultQueueCallbackA copy error 32 "C:\\windows\\msdownld.tmp\\AS008083.tmp\\OLEAUT32.DLL" -> "c:\\windows\\system\\OLEAUT32.DLL"
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO

---

### Post by StacyWebb on 2005-03-16
Just out of curiousity is there a reason you need IE? Becaus e you can install the Firefox extension "UserAgent Switcher" and the select identify browser as IE on WinXp. That should solve any web page connection errors (such as 'this page is best viewed with IE6") but If you really need IE trying installing it right after you install DCOM95 don't install 98 just to see if thats where your error comes from.

---

### Post by canglan on 2005-03-17
No, I don't need IE. However, winetools was telling me that IE is **required**. And furthermore, IE and other software were all failed to install. 

The C_Drive directory is set to root:root, is that correct? And if so, what CHMOD permission do I need to set it? Or maybe someone could look into the error message for me and find out what was happening?

Thank you very much.

---

