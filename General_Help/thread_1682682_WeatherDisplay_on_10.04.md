---
title: "WeatherDisplay on 10.04"
date: 2011-02-06
forum: General Help
---

### Post by kp4djt on 2011-02-06
Folks,
I have been trying to get WeatherDisplay to run on my 10.04 machines so I can gather info off of a weather station I have. 

When I run the program from a command line I see the following which I am assuming are errors due to something missing:

kp4djt@garrobo:~/bin/wdisplay$ ./GoWeather.sh 
[HINT] TWinControl.CreateWnd creating Handle during loading MainForm:TMainForm csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Formtempdials:TFormtempdials csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading weatherdials:Tweatherdials csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading graphform:Tgraphform csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Formpercentdir:TFormpercentdir csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading averages:Taverages csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading PageControl1:TPageControl csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading TabSheet1:TTabSheet csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Splitter1:TSplitter csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Button5:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Button6:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading ProgressBar1:TProgressBar csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Button1:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Button4:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading BitBtn1:TBitBtn csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading printpage:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Button8:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Button9:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading GroupBox5:TGroupBox csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading SpinEditday:TSpinEdit csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading SpinEditmonthsel:TSpinEdit csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading SpinEdityearsel:TSpinEdit csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Button14:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Button26:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Button3:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading GroupBox8:TGroupBox csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading CheckBoxsoil:TCheckBox csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading SpinEditgdd:TSpinEdit csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading CheckBoxusemydatarecords:TCheckBox csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading SpinEditheatdegrees:TSpinEdit csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading SpinEditheatdegrees2:TSpinEdit csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading logmemo2:TMemo csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading logmemo:TMemo csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading TabSheet2:TTabSheet csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Button23:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading BitBtn2:TBitBtn csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading ProgressBar3:TProgressBar csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Button21:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading GroupBox6:TGroupBox csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading SpinEdit2:TSpinEdit csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading SpinEdit3:TSpinEdit csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Button16:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Button30:TButton csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading CheckBoxmaxminaverage:TCheckBox csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Memonoaa:TMemo csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading TabSheet3:TTabSheet csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading Formfwigraph:TFormfwigraph csDesigning=False

I am thinking that it maybe this package as indicated in a
readme.txt file:
Also. GTK is needed to be installed for the GTK version
use
sudo apt-get install gtk+ gdk-pixbuf
if not installed

I have tried to locate this one but no luck. Any one have
any ideas or are you running WeatherDisplay under Ubuntu?

Please do not recommend some of the other weather apps that
are in the downloads, this has to interact with a wireless
USB connected station and none of them work.

The weather station I am using is a La Crosse WS-2812U-IT
The station connects to a computer using a wireless USB
dongle WeatherDisplay appears to be the only Linux app that
can capture the data stream and display it.

---

### Post by Bryan55 on 2011-02-06
I prosume you know there is a Linux section on the Weather Display forum?

[http://www.weather-watch.com/smf/index.php/board,21.0.html](http://www.weather-watch.com/smf/index.php/board,21.0.html)

Bryan

---

### Post by kp4djt on 2011-02-06
Bryan,
Yes I did, I wanted to drop a note here as I usually get good results
from the Ubuntu list first. 

I will try there. I found out how to get my USB wireless dongle recognised
there but the program does not appear to want to capture the WS-2812U info
correctly. I have tried both the 23xx and the 36xx selections but no joy.
So I have to see what else I can dig up on that.

---

