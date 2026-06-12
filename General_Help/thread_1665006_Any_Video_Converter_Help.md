---
title: "Any Video Converter Help"
date: 2011-01-11
forum: General Help
---

### Post by Jamezo97 on 2011-01-11
I was wondering if anyone has found a way to make Any Video Converter work in Ubuntu.
I opened up a terminal, and told wine to run the exe file. I went through all of the steps in the installer and it seemed to finish without a hitch...
> 
james@james-ubuntu:~$ cd ./downlaods
bash: cd: ./downlaods: No such file or directory
james@james-ubuntu:~$ cd Downloads
james@james-ubuntu:~/Downloads$ wine ./avc-free.exe
fixme:win:DisableProcessWindowsGhosting : stub
fixme:msg:ChangeWindowMessageFilter c046 00000001
fixme:msg:ChangeWindowMessageFilter c046 00000001
fixme:msg:ChangeWindowMessageFilter c046 00000001
fixme:msg:ChangeWindowMessageFilter c046 00000001
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption Unhandled dwOption 4
fixme:wininet:INET_QueryOption Unhandled dwOption 5
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption Unhandled dwOption 4
fixme:wininet:INET_QueryOption Unhandled dwOption 5
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption Unhandled dwOption 4
fixme:wininet:INET_QueryOption Unhandled dwOption 5
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption Unhandled dwOption 4
fixme:wininet:INET_QueryOption Unhandled dwOption 5
fixme:ole:CoCreateInstance no instance created for interface {ea1afb91-9e28-4b86-90e9-9e9f8a5eefaf} of class {56fdf344-fd6d-11d0-958a-006097c9a090}, hres is 0x80004002
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Program Files\\AnvSoft\\Any Video Converter\\unins000.exe") stub
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption Unhandled dwOption 4
fixme:wininet:INET_QueryOption Unhandled dwOption 5
james@james-ubuntu:~/Downloads$ cd
Then once it was installed I started the program:
> 
james@james-ubuntu:~$ anyvideoconverter
anyvideoconverter: command not found
james@james-ubuntu:~$ wine anyvideoconverter
wine: cannot find L"C:\\windows\\system32\\anyvideoconverter.exe"
james@james-ubuntu:~$ cd /home/james/.wine/dosdevices/c:/Program Files/AnvSoft/Any Video Converter
bash: cd: /home/james/.wine/dosdevices/c:/Program: No such file or directory
james@james-ubuntu:~$ cd '/home/james/.wine/dosdevices/c:/Program Files/AnvSoft/Any Video Converter'
[EMAIL="james@james-ubuntu:%7E/.wine"]james@james-ubuntu:~/.wine[/EMAIL]/dosdevices/c:/Program Files/AnvSoft/Any Video Converter$ wine VideoConverter.exe
1294788165 INFO main : ---------------------------------------------------------------------------
1294788165 INFO main : Logger initialized.
1294788165 INFO main : Windows Version Information:
1294788165 INFO main :     Major Version = 5
1294788165 INFO main :     Minor Version = 1
1294788165 INFO main :     Build Number = 2600
1294788165 INFO main :     Platform Id = 2
1294788165 INFO main :     Version  = S
1294788165 INFO main :     Windows XP
1294788165 INFO main : Loading program Any Video Converter ...
1294788165 INFO main : Loading resource dll [C:\Program Files\AnvSoft\Any Video Converter\avcres.dll] ...
1294788165 INFO main : Set resource handle as resource DLL successfully.
1294788165 INFO main : DB2 SQLite Version: 3.5.1
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
1294788165 INFO main : Creating history table
1294788165 INFO main : Creating profiles table
1294788165 INFO main : Creating groups table
1294788165 INFO main : Loading program Any Video Converter ...
fixme:win:EnumDisplayDevicesW ((null),0,0x3257a8,0x00000000), stub!
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
1294788165 INFO main : Winsock and OLE initialized.
1294788165 INFO main : Common controls and shell manager initialized.
1294788165 INFO main : BCG library initialized.
1294788165 INFO main : Loading profiles...
1294788170 INFO main : Starting main dialog ...
fixme:win:LockWindowUpdate (0x10066), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
1294788172 INFO CVideoConverterDlg OnInitDialog: Initializing main dialog ...
1294788172 INFO CVideoConverterDlg OnInitDialog: Loading accelerators ...
1294788172 INFO CVideoConverterDlg OnInitDialog: List control initialized.
1294788172 INFO CVideoConverterDlg OnInitDialog: Panel preview initialized.
1294788173 INFO CVideoConverterDlg OnInitDialog: Panel profile combo list initialized.
1294788173 INFO CVideoConverterDlg OnInitDialog: Panel property list initialized.
1294788173 INFO CVideoConverterDlg OnInitDialog: Version : Any Video Converter 3.1.7
1294788173 INFO CVideoConverterDlg OnInitDialog: Registered version.
fixme:win:LockWindowUpdate (0x10066), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
1294788174 INFO CVideoConverterDlg : Creating events for pipe read/write...
1294788174 INFO CVideoConverterDlg : Creating online video downloader...
1294788174 INFO CVideoConverterDlg : Setting YouTube output folder: [C:\users\james\My Documents\Any Video Converter]...
1294788174 INFO CVideoConverterDlg : Main dialog initialized.
1294788174 INFO CVideoConverterDlg : Internet connection available, checking update version...
1294788174 INFO CheckVersionThread : Checking upgrade version...
1294788174 INFO CheckVersionThread : Downloading INI file C:\Program Files\AnvSoft\Any Video Converter\version.ini...
1294788174 INFO CCheckUpdateDlg::GetFile : Downloading file from url: [http://update.any-video-converter.com/avc_free_version.ini](http://update.any-video-converter.com/avc_free_version.ini)
fixme:dciman:DCICreatePrimary 0x710 0x6aa2ac
1294788175 INFO CheckVersionThread : No new version available: 3.1.7
1294788230 INFO CVideoConverterDlg : Panel profile combo list initialized.
That seemed to go OK, except for when I try to choose a different codec to convert to, it only allows me to choose flv or mp4, because the drop down list disappears when my house hovers over it...
Any way, I went to convert a video:

> 
1294788354 INFO CVideoConverterDlg EncodeVideos: Encoding 1 videos, profile: Flash Video Movie (*.flv)
1294788354 INFO CVideoConverterDlg EncodeVideos: cmd.exe /c ""C:\Program  Files\AnvSoft\Any Video Converter\mencoder.exe" -mc 0 -af volnorm -vf  scale=320:-2,expand=:240:::,crop=320:240,harddup -ofps 25 -srate 44100  -oac mp3lame -lameopts abr:br=64 -ovc lavc -of lavf -lavfopts format=flv  -lavcopts vcodec=flv:vbitrate=512:mbd=2:mv0:trell:v4mv:cbp:last_pred=3  -o "C:\users\james\Desktop\FLV\intro.flv"  "C:\users\james\Desktop\intro.mp4" 2>"C:\users\james\Temp\menc_err2""
1294788357 INFO CVideoConverterDlg EncodeVideos: Command execute failed: , 9009
1294788357 INFO CVideoConverterDlg EncodeVideos: Encode a single video file finished.
1294788357 INFO CVideoConverterDlg EncodeVideos: Encode all videos finished
1294788382 INFO CVideoConverterDlg : Panel profile combo list initialized.
1294788384 INFO CVideoConverterDlg : Panel profile combo list initialized.
And it quickly stopped and said that the conversion failed...
And then i tried to convert it to MP4...

> 
1294788387 INFO CVideoConverterDlg EncodeVideos: Encoding 1 videos, profile: Mobile Phone MPEG-4 Movie (*.mp4)
1294788388 INFO CVideoConverterDlg EncodeVideos: cmd.exe /c ""C:\Program  Files\AnvSoft\Any Video Converter\mencoder.exe" -mc 0 -af volnorm -vf  scale=176:-2,expand=:144:::,crop=176:144,harddup -srate 11025 -ofps 15  -oac faac -faacopts br=64:mpeg=4:object=2 -ovc lavc -ffourcc DIVX  -lavcopts vcodec=mpeg4:mbd=2:trell:autoaspect:vbitrate=128:vhq -o  "C:\users\james\Desktop\MOBILE_MP4\intro_mpeg4.avi"  "C:\users\james\Desktop\intro.mp4" 2>"C:\users\james\Temp\menc_err2""
1294788389 INFO CVideoConverterDlg EncodeVideos: Command execute failed: , 9009
1294788389 INFO CVideoConverterDlg EncodeVideos: Encode a single video file finished.
1294788389 INFO CVideoConverterDlg EncodeVideos: Encode all videos finished
^Cjames@james-ubuntu:~/.wine/dosde
And it did the same thing... It said that the conversion had failed.
So: Does anyone know how to fix this? Maybe installing something from winetricks?
Thanks

---

### Post by 3rdalbum on 2011-01-11
Rather than try and shoehorn Windows programs onto your Linux desktop, have you tried native Linux software for converting videos? Handbrake is a good one - you can get the simple instructions for installing it from: [http://www.jonathanmoeller.com/screed/?p=2592](http://www.jonathanmoeller.com/screed/?p=2592)

---

