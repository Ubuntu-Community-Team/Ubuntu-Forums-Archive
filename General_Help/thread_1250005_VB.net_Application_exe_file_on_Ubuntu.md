---
title: "VB.net Application exe file on Ubuntu"
date: 2009-08-26
forum: General Help
---

### Post by arvin555 on 2009-08-26
Hi,  relatively newbie with Linux/Ubunutu, and deep in trying out things that turn out to be a bit difficult.

I am using Jaunty and have installed Wine and Monodev (from Add/remove)

I am trying to run an exe file from [http://www.carnivoren.info/](http://www.carnivoren.info/)  it was made using VB.Net on Framework 2.0.  

I have already installed it through Wine.  However I could not open it at all.  I click on the Icon on wine. 

I also tried using the command  "mono CP-GrowList.exe" from Terminal, won't go either, there are errors.

> ** (CP-GrowList.exe:8510): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
The entry point method could not be loaded


Any ideas on how I can make this application run on Ubuntu?

I have no experience with VB programming and the likes, so trying to compile the same program on monodev might not be possible due to my limited knowledge, unless someone is willing to walk me through it.

Looking forward to suggestions.

TTFN
Arvin

---

### Post by Ozitraveller on 2009-08-26
"made using VB.Net on Framework 2.0"

If you were running windows I'd say you needed to install the dotnet runtime.

[http://www.microsoft.com/downloads/details.aspx?FamilyID=0856EACB-4362-4B0D-8EDD-AAB15C5E04F5&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=0856EACB-4362-4B0D-8EDD-AAB15C5E04F5&displaylang=en)

I have no idea whether that will work in wine. Probably not.


EDIT: operating system components	  	 Framework 2.0

---

### Post by directhex on 2009-08-26
> **arvin555 said:**
> Hi,  relatively newbie with Linux/Ubunutu, and deep in trying out things that turn out to be a bit difficult.

I am using Jaunty and have installed Wine and Monodev (from Add/remove)

I am trying to run an exe file from [http://www.carnivoren.info/](http://www.carnivoren.info/)  it was made using VB.Net on Framework 2.0.  

I have already installed it through Wine.  However I could not open it at all.  I click on the Icon on wine. 

I also tried using the command  "mono CP-GrowList.exe" from Terminal, won't go either, there are errors.



Any ideas on how I can make this application run on Ubuntu?

I have no experience with VB programming and the likes, so trying to compile the same program on monodev might not be possible due to my limited knowledge, unless someone is willing to walk me through it.

Looking forward to suggestions.

TTFN
Arvin

[libmono-microsoft-visualbasic8.0-cil](apt:libmono-microsoft-visualbasic8.0-cil)

---

### Post by arvin555 on 2009-08-26
Had problems getting the lib that you suggested Directhex so I did a search and found it here:

[http://packages.ubunut.com/jaunty/all/libmono-microsoft-visualbasic8.0-cil/download](http://packages.ubunut.com/jaunty/all/libmono-microsoft-visualbasic8.0-cil/download)

I am now installing it, and will test as soon as finish and report back.

I'm back, and unfortunately althought there was initial "movement" when a small window with a logo appeared, it disappeared and nothing happened.  I used Terminal again to run the file, Wine doesn't do anything.

I am not sure if the following will help:

> Unhandled Exception: System.InvalidOperationException: Error message not available. ---> System.EntryPointNotFoundException: SystemParametersInfo
  at (wrapper managed-to-native) Dotnetrix.NativeMethods:SystemParametersInfo (int,int,int&,int)
  at Dotnetrix.Controls.TabControlEX.AcceleratorVisible () [0x00000] 
  at Dotnetrix.Controls.TabControlEX..ctor () [0x00000] 
  at (wrapper remoting-invoke-with-check) Dotnetrix.Controls.TabControlEX:.ctor ()
  at Carnivoren_Grow_List.frmMain.InitializeComponent () [0x00000] 
  at (wrapper remoting-invoke-with-check) Carnivoren_Grow_List.frmMain:InitializeComponent ()
  at Carnivoren_Grow_List.frmMain..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at Carnivoren_Grow_List.My.MyProject+MyForms.Create__Instance__[frmMain] (Carnivoren_Grow_List.frmMain Instance) [0x00000] 
  at Carnivoren_Grow_List.My.MyProject+MyForms.get_frmMain () [0x00000] 
  at Carnivoren_Grow_List.frmStart.frmStart_Load (System.Object sender, System.EventArgs e) [0x00000] 
  at System.Windows.Forms.Form.OnLoad (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.Form.OnLoadInternal (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.Form.OnCreateControl () [0x00000] 
  at System.Windows.Forms.Control.CreateControl () [0x00000] 
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Form.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.NativeWindow.WndProc (IntPtr hWnd, Msg msg, IntPtr wParam, IntPtr lParam) [0x00000] 
  at System.Windows.Forms.XplatUIX11.SendMessage (IntPtr hwnd, Msg message, IntPtr wParam, IntPtr lParam) [0x00000] 
  at System.Windows.Forms.XplatUIX11.MapWindow (System.Windows.Forms.Hwnd hwnd, WindowType windows) [0x00000] 
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] 
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] 
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams cp) [0x00000] 
  at System.Windows.Forms.Control.CreateHandle () [0x00000] 
  at System.Windows.Forms.Form.CreateHandle () [0x00000] 
  at System.Windows.Forms.Control.CreateControl () [0x00000] 
  at System.Windows.Forms.Control.SetVisibleCore (Boolean value) [0x00000] 
  at System.Windows.Forms.Form.SetVisibleCore (Boolean value) [0x00000] 
  at System.Windows.Forms.Control.set_Visible (Boolean value) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Control:set_Visible (bool)
  at System.Windows.Forms.Application.RunLoop (Boolean Modal, System.Windows.Forms.ApplicationContext context) [0x00000] 
  at System.Windows.Forms.Application.Run (System.Windows.Forms.ApplicationContext context) [0x00000] 
  at System.Windows.Forms.Application.Run (System.Windows.Forms.Form mainForm) [0x00000] 
  at Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun () [0x00000] 
  at Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run (System.String[] commandLine) [0x00000] 
  at Carnivoren_Grow_List.My.MyApplication.Main (System.String[] Args) [0x00000] 


---

### Post by directhex on 2009-08-26
> **arvin555 said:**
> Had problems getting the lib that you suggested Directhex so I did a search and found it here:

[http://packages.ubunut.com/jaunty/all/libmono-microsoft-visualbasic8.0-cil/download](http://packages.ubunut.com/jaunty/all/libmono-microsoft-visualbasic8.0-cil/download)

I am now installing it, and will test as soon as finish and report back.

I'm back, and unfortunately althought there was initial "movement" when a small window with a logo appeared, it disappeared and nothing happened.  I used Terminal again to run the file, Wine doesn't do anything.

I am not sure if the following will help:

The app makes use of non-portable stuff (i.e. it's calling into Windows-only C libraries), and won't run on Linux with Mono.

---

### Post by MartinEve on 2009-08-26
If you are attempting to run .NET applications under Wine, you'll need to install the runtime: [http://appdb.winehq.org/appview.php?iVersionId=3754](http://appdb.winehq.org/appview.php?iVersionId=3754)

---

### Post by arvin555 on 2009-08-26
Thanks guys!

Didn't want to give up that easily, so I tried to install .net framework on wine.  Realized a lot of bugs and problems on that too, I'm still stuck with not being able to install Frameworks 2.0 and I haven't been able to test that application.

Will post back if there is any positive outcome. 

TTFN
Arvin

---

### Post by arvin555 on 2009-09-18
Very sorry to say that I came to a lot of dead ends.  I think that installing Netframework should work fix my problem of using the application, but as of now it is really quite hard to install frameworks 2.0 on Jaunty. :(  Quite complicated and a lot of bugs to fix.  I spent 1 whole day trying different suggestions, no go :(

Will stop trying now, hopefully when we get an updated version of Ubuntu or if someone finds a way for easy integration of the two... maybe.

TTFN
Arvin

---

### Post by directhex on 2009-09-19
> **arvin555 said:**
> Very sorry to say that I came to a lot of dead ends.  I think that installing Netframework should work fix my problem of using the application, but as of now it is really quite hard to install frameworks 2.0 on Jaunty. :(  Quite complicated and a lot of bugs to fix.  I spent 1 whole day trying different suggestions, no go :(

Will stop trying now, hopefully when we get an updated version of Ubuntu or if someone finds a way for easy integration of the two... maybe.

TTFN
Arvin

It's a Windows-only app. That it even considers running is madness itself - it's like trying to feed a Nintendo 64 cartridge into a Playstation and wondering why nothing works

Making cross-platform VB.NET apps is easy. It simply requires competent developers.

---

### Post by arvin555 on 2009-09-19
Thanks, for the comment, yeah I totally agree that my problem would have been easily solved if the programmer just made it to be compatible/cross platoform, but unfortunatley he just made it for windows, primarily.  I guess if I really needed it, I just boot using Windows... but then it's just a hassle and so it turns out to be not worth the hassle of double booting, it's been probably a month now since I last booted on Windows with my home PC.... sounds like how someone introduces himself to a substance abuse group :)  

TTFN
Arvin

---

