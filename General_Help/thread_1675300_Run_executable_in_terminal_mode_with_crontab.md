---
title: "Run executable in terminal mode with crontab"
date: 2011-01-25
forum: General Help
---

### Post by JCM_Pico on 2011-01-25
Hello there,
I have some routines scheduled in crontab, but in one of theme there is a command that only runs in terminal (matlab -nojvm) , is there any way to force the crontab to run in terminal?

---

### Post by psusi on 2011-01-25
No.  The whole point of cron is that it runs things regardless of who, if anyone, is logged in on any given terminal.  The output of the programs it runs is directed to a file that cron emails you when the job is done, not a terminal.

I am sure that matlab can be run without an interactive user at a terminal.

---

### Post by JCM_Pico on 2011-01-25
you're right, I can run matlab with crontab without a user terminal...
But I can not create images and save them.
I'm using a script to generate some figures, every day. with crontab I'm being able to make all the calc, but it does not save the figures.
Any idea ?

---

### Post by psusi on 2011-01-25
It doesn't have a switch you can pass telling it where to save the results?  Or can read commands from stdin, one of which can be a command to save the results somewhere?

---

### Post by JCM_Pico on 2011-01-25
> **psusi said:**
> It doesn't have a switch you can pass telling it where to save the results?  Or can read commands from stdin, one of which can be a command to save the results somewhere?

I'm using the matlab script to save the figures in a folder. But it matlab wont generate the figures when i use Crontab. If i run the bash script, the sane that i use in Crontab, but in terminal it runs without any problem...

---

### Post by Cheesehead on 2011-01-25
If the script runs fine in terminal but fails in cron, the three most commom problems are:

1) Need to use full paths ('/usr/bin/touch' instead of 'touch', '/home/me/output' instead of '~/output')

2) Different environment. Cron doesn't know or care which display you are usiing, your .bashrc, or anything else abour your user-level environment. If your scripts need to know these, you must explicitly tell them.

3) Improper usage of permissions or improper installation of the crontab. Running root scripts as a user. Running user scripts as root. Installing crontabs using weird methods instead of the 'crontab' command

Why don't you show us the crontab and script?
The symptoms you describe sound like #1 or #2.

---

### Post by JCM_Pico on 2011-01-25
> **Cheesehead said:**
> If the script runs fine in terminal but fails in cron, the three most commom problems are:

1) Need to use full paths ('/usr/bin/touch' instead of 'touch', '/home/me/output' instead of '~/output')

2) Different environment. Cron doesn't know or care which display you are usiing, your .bashrc, or anything else abour your user-level environment. If your scripts need to know these, you must explicitly tell them.

3) Improper usage of permissions or improper installation of the crontab. Running root scripts as a user. Running user scripts as root. Installing crontabs using weird methods instead of the 'crontab' command

Why don't you show us the crontab and script?
The symptoms you describe sound like #1 or #2.

Its not #1 =)

and here follows the crontab:

```
00 05 * * * /home/user/Desktop/Project/matlab_runner.sh
```and here the sh script:
```

mv temp4 station_out.m
rm temp*
echo "running m-file"
matlab -nojvm -nosplash -r "station_out;exit"

echo "done"

echo "Changing station_out.m"

sed 5s/.*/"dia = '$(date --date='1 days' +%d)';"/ station_out.m > temp1
sed 6s/.*/"mes = '$(date --date='1 days' +%m)';"/ temp1 > temp2
sed 7s/.*/"ano = '$(date --date='1 days' +%Y)';"/ temp2 > temp3

sed 37s/.*/"horas = ['$(date --date='1 days' +%y-%m-%d)-00h'; '$(date --date='1 days' +%y-%m-%d)-12h'; '$(date --date='2 days' +%y-%m-%d)-00h'; '$(date --date='2 days' +%y-%m-%d)-12h'; '$(date --date='3 days' +%y-%m-%d)-00h'; '$(date --date='3 days' +%y-%m-%d)-12h'; '$(date --date='4 days' +%y-%m-%d)-00h'];"/ temp3 > temp4
mv temp4 station_out.m
rm temp*
echo "running m-file"
matlab -nojvm -nosplash -r "station_out;exit"

echo "done"

```I can post the matlab script if needed .... 

hope it helps

---

### Post by JCM_Pico on 2011-01-26
any idea?

---

### Post by Cheesehead on 2011-01-26
Yeah, there's lots of #1 (need to use full paths). 

For example:
```
mv temp4 station_out.m     # current
/bin/mv /home/USER/temp /home/USER/stationout.m   # full paths
```
It really is the most common reason for cron-launched scripts to fail.

Since you wrote that the crontab runs, that's not the problem.
Since you wrote that the script does run matlab, that's probably not the problem...though the lack of full paths may cause unintended consequences.

For example, matlab may be looking for an environment that cron simply does not provide...so full paths within your matlab script are also important.

If full paths in the shell script and matlab script doesn't fix the problem, then go ahead and post the matlab script.

---

### Post by JCM_Pico on 2011-01-27
> **Cheesehead said:**
> Yeah, there's lots of #1 (need to use full paths). 

For example:
```
mv temp4 station_out.m     # current
/bin/mv /home/USER/temp /home/USER/stationout.m   # full paths
```It really is the most common reason for cron-launched scripts to fail.

Since you wrote that the crontab runs, that's not the problem.
Since you wrote that the script does run matlab, that's probably not the problem...though the lack of full paths may cause unintended consequences.

For example, matlab may be looking for an environment that cron simply does not provide...so full paths within your matlab script are also important.

If full paths in the shell script and matlab script doesn't fix the problem, then go ahead and post the matlab script.

Ok, this will be a long post.....

```

00 05 * * * /home/user/Desktop/Project/get_forc_WP.sh
30 05 * * * /home/user/Desktop/Project/wrf_runner.sh
37 15 * * * /home/user/Desktop/Project/matlab_runner.sh
```

 The last entry is just for testing, I call the script within the wrf_runner.sh

The first two scripts in the crontab work without any problem and I'll post here...

_***[SIZE=3]get_forc_WP.sh[/SIZE]***_
```
#!/bin/bash
cd /home/weather-pirate/WRF/analise/
rm *
begindate=$(date +%Y%m%d)

analize=00

# if [ $# -lt 2 ]; then
#   echo "Usage: $0 <begindate(yyyymmdd)> <analize>"
#   exit 1
# fi

urlpath="ftp://tgftp.nws.noaa.gov/SL.us008001/ST.opnl/MT.gfs_CY."
some="RD."
fileprefix="PT.grid_DF.gr2"
filesufix_00="fh.0000_tl.press_gr.0p5deg"
filesufix_06="fh.0006_tl.press_gr.0p5deg"
filesufix_12="fh.0012_tl.press_gr.0p5deg"
filesufix_18="fh.0018_tl.press_gr.0p5deg"
filesufix_24="fh.0024_tl.press_gr.0p5deg"
filesufix_30="fh.0030_tl.press_gr.0p5deg"
filesufix_36="fh.0036_tl.press_gr.0p5deg"
filesufix_42="fh.0042_tl.press_gr.0p5deg"
filesufix_48="fh.0048_tl.press_gr.0p5deg"
filesufix_54="fh.0054_tl.press_gr.0p5deg"
filesufix_60="fh.0060_tl.press_gr.0p5deg"
filesufix_66="fh.0066_tl.press_gr.0p5deg"
filesufix_72="fh.0072_tl.press_gr.0p5deg"
filesufix_78="fh.0078_tl.press_gr.0p5deg"
filesufix_84="fh.0084_tl.press_gr.0p5deg"
filesufix_90="fh.0090_tl.press_gr.0p5deg"
filesufix_96="fh.0096_tl.press_gr.0p5deg"

filetoextract_00=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_00
filetoextract_06=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_06
filetoextract_12=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_12
filetoextract_18=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_18
filetoextract_24=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_24
filetoextract_30=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_30
filetoextract_36=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_36
filetoextract_42=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_42
filetoextract_48=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_48
filetoextract_54=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_54
filetoextract_60=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_60
filetoextract_66=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_66
filetoextract_72=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_72
filetoextract_78=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_78
filetoextract_84=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_84
filetoextract_90=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_90
filetoextract_96=$urlpath$analize/$some$begindate/$fileprefix/$filesufix_96

# wget -b "$filetoextract_00"
# wget -b "$filetoextract_06"
# wget -b "$filetoextract_12"
# wget -b "$filetoextract_18"
wget -b "$filetoextract_24"
wget -b "$filetoextract_30"
wget -b "$filetoextract_36"
wget -b "$filetoextract_42"
wget -b "$filetoextract_48"
wget -b "$filetoextract_54"
wget -b "$filetoextract_60"
wget -b "$filetoextract_66"
wget -b "$filetoextract_72"
wget -b "$filetoextract_78"
wget -b "$filetoextract_84"
wget -b "$filetoextract_90"
wget -b "$filetoextract_96"

echo "Wait for it" 
```_***[SIZE=3]wrf_runner.sh[/SIZE]***_
```
#!/bin/sh

####################################
#
#      Clear and run WRF.
# Made to Project Weather-pirate
# By JCarlos
#
####################################

# Call the script to change the nalist days
cd /home/weather-pirate/Desktop/Project_WP/
./day_changer.sh

grib_loc="/home/weather-pirate/WRF/analise/"
#cd $grib_loc
#rm *
#echo "Last grib files deleted"
#get_forc_PWP.sh
#echo "Getting grib files"

cd /home/weather-pirate/WRF/WPS/
rm met_* FILE* GRIB*
./link_grib.csh $grib_loc
wait
echo "Last run files deleted"
echo "Running ungrib.exe"
./ungrib.exe
echo "Runing metgrind.exe"
./metgrid.exe

cd /home/weather-pirate/WRF/WRFV3/run
rm met_* wrfinput_d0* wrfb* wrfout*
ln -sf /home/weather-pirate/WRF/WPS/met_* .
echo "Running real.exe"
./real.exe
echo "Running wrf.exe"
./wrf.exe
echo "output in nohup.out"

cd /home/weather-pirate/Desktop/Projecto_WP/
./matlab_runner.sh
```Both work well, except one thing, in wrf_runner.sh it does not execute ./matlab_runner.sh ... All other files are created and deleted, and this is running for almost a month....

The last entry in crontab is  used to debug, since matlab_runner.sh is not running...
[B][I][U][SIZE=3]
matlab_runner.sh[/SIZE][/U][/I][/B]
```
#!/bin/sh

####################################
#
#      Run post-processing of WRF.
# Made to Project Weather-pirate
# By JCarlos
#
####################################

# station_out.m
echo "Changing station_out.m"

/bin/sed 5s/.*/"dia = '$(date --date='1 days' +%d)';"/ /home/weather-pirate/Desktop/Project_WP/station_out.m > /home/weather-pirate/Desktop/Project_WP/temp1
/bin/sed 6s/.*/"mes = '$(date --date='1 days' +%m)';"/ /home/weather-pirate/Desktop/Project_WP/temp1 > /home/weather-pirate/Desktop/Project_WP/temp2
/bin/sed 7s/.*/"ano = '$(date --date='1 days' +%Y)';"/ /home/weather-pirate/Desktop/Project_WP/temp2 > /home/weather-pirate/Desktop/Project_WP/temp3

sed 8s/.*/"horas = ['$(date --date='1 days' +%y-%m-%d)-00h'; '$(date --date='1 days' +%y-%m-%d)-12h'; '$(date --date='2 days' +%y-%m-%d)-00h'; '$(date --date='2 days' +%y-%m-%d)-12h'; '$(date --date='3 days' +%y-%m-%d)-00h'; '$(date --date='3 days' +%y-%m-%d)-12h'; '$(date --date='4 days' +%y-%m-%d)-00h'];"/ /home/weather-pirate/Desktop/Project_WP/temp3 > /home/weather-pirate/Desktop/Project_WP/temp4

/bin/mv /home/weather-pirate/Desktop/Project_WP/temp4 /home/weather-pirate/Desktop/Project_WP/station_out.m
/bin/rm /home/weather-pirate/Desktop/Project_WP/temp*
echo "running m-file"
cd /home/weather-pirate/Desktop/Project_WP/
/usr/local/bin/matlab -nojvm -nosplash -r "station_out;exit"
## matlab -r "station_out;exit"

echo "done"
```This script works in terminal (./matlab_runner.sh), but not in crontab...
if when I call matlab I use /usr/local/bin/matlab -nojvm -nosplash -r "/home/weather-pirate/Desktop/Project_WP/station_out;exit" matlab does not run even in terminal.

The matlab script I'm trying to run....

[SIZE=3]_***station_out.m***_[/SIZE]
```
% station_out --> Plot de várias variáveis para dominio 3 PWP
%
%Jcarlos
clear all; close all; clc;
dia = '15';
mes = '01';
ano = '2011';
horas = ['13 Jan-00h'; '13 Jan-12h'; '14 Jan-00h'; '14 Jan-12h'; '15 Jan-00h'; '15 Jan-12h'; '16 Jan-00h'];
addpath /home/weather-pirate/WRF/WRFV3/run/
out = netcdf(['wrfout_d02_' ano '-' mes '-' dia '_00:00:00']); % Para poder fazer a aquisição das variaveis

%% DOMINIO MADALENA
latn = 28;                  
lonn = 30;                 
lev = 1;

%% VARS
u = out{'U10'}(:,latn,lonn);      
v = out{'V10'}(:,latn,lonn);        
P = out{'P'}(:,lev,latn,lonn);         
PB = out{'PB'}(:,lev,latn,lonn);
p = P + PB;                           
clear P PB;                  
tmp = out{'T2'}(:,latn,lonn);

rainc = out{'RAINC'}(:,latn+5,lonn);      
rainnc = out{'RAINNC'}(:,latn,lonn);
rain_temp = [0; (rainc + rainnc)];

n = length(u); 
rain = zeros(n,1);
for i = 1:n
   rain(i,:,:) = rain_temp(i+1) - rain_temp(i);
end 
clear rain_temp rainnc rainca

clear out

u = squeeze(u(:,1,1));            v = squeeze(v(:,1,1));      

%% FIGURAS
a = exist('~/Desktop/forcast_temp/','dir');
if a == 7
    
else
    if a == 0
    !mkdir ~/Dropbox/forcast_temp/
    !mkdir ~/Dropbox/forcast_temp/st/
    end
end
clear a

%Precipitação
scrsz = get(0,'ScreenSize');
fig = figure('Position',[1 scrsz(4)/2 scrsz(3)/1.5 scrsz(4)/2.6]);
plot(rain,'linewidth',2)
xlabel('tempo (h)','fontsize',11,'fontweight','b');
ylabel('Precipitação (mm/h)','fontsize',11,'fontweight','b')
set(gca,'XTick',0:12:n);
set(gca,'XTickLabel',horas,'fontsize',10);

print('-dpng ','-r300','~/Dropbox/forcast_temp/st/rain.png');




%Pressão
scrsz = get(0,'ScreenSize');
fig = figure('Position',[1 scrsz(4)/2 scrsz(3)/1.5 scrsz(4)/2.6]);
plot(p*1e-2,'linewidth',2)
xlabel('tempo (h)','fontsize',11,'fontweight','b');
ylabel('Pressão (hPa)','fontsize',11,'fontweight','b')
set(gca,'XTick',0:12:n);
set(gca,'XTickLabel',horas,'fontsize',10);

print('-dpng ','-r300','~/Dropbox/forcast_temp/st/hp.png');

%Temperaura 2m
scrsz = get(0,'ScreenSize');
fig = figure('Position',[1 scrsz(4)/2 scrsz(3)/1.5 scrsz(4)/2.6]);
plot(tmp - 273.15,'linewidth',2)
xlabel('tempo (h)','fontsize',11,'fontweight','b');
ylabel('Temperatura (^\circ C)','fontsize',11,'fontweight','b')
set(gca,'XTick',0:12:n);
set(gca,'XTickLabel',horas,'fontsize',10);

print('-dpng ','-r300','~/Dropbox/forcast_temp/st/tmp.png');

%Vento
scrsz = get(0,'ScreenSize');
fig = figure('Position',[1 scrsz(4)/2 scrsz(3)/1.5 scrsz(4)/2.6]);
feather(u,v)
xlabel('tempo (h)','fontsize',11,'fontweight','b');
ylabel('Intensidade (nós)','fontsize',11,'fontweight','b')
ylim([-50 50]);
set(gca,'XTick',0:12:n,'YTick',-50:10:50);
set(gca,'XTickLabel',horas,'fontsize',10);

% Create line
annotation(fig,'line',[0.158264947245018 0.207502930832356],[0.774974025974026 0.772727272727273]);
% Create textbox
annotation(fig,'textbox',[0.206882352941177 0.752659574468085 0.0151290322580645 0.0452127659574468],'String',{'E'},'FitBoxToText','off','LineStyle','none');
% Create textbox
annotation(fig,'textbox',[0.137622390891841 0.763297872340426 0.0189240986717268 0.0372340425531915],'String',{'W'},'FitBoxToText','off','LineStyle','none');
% Create textbox
annotation(fig,'textbox',[0.169368811049739 0.883116883116883 0.0201019929660024 0.0357142857142863],'String',{'N'},'FitBoxToText','off','LineStyle','none');
% Create arrow
annotation(fig,'arrow',[0.182883939038687 0.181711606096131],    [0.710038961038961 0.863636363636364]);
% Create textbox
annotation(fig,'textbox',[0.172503188879076 0.666067974578613 0.014180265654649 0.050531914893617],'String',{'S'},'FitBoxToText','off','LineStyle','none');

print('-dpng ','-r300','~/Dropbox/forcast_temp/st/vento.png');

```Thank you for all the attention and the help that all of you have given me so far :P

---

### Post by JCM_Pico on 2011-01-31
Problem solved.
Matlab needed a graphical environment to create the figures.
Using xvfb-run its possible to save those figures  
[http://en.wikipedia.org/wiki/Xvfb](http://en.wikipedia.org/wiki/Xvfb)

---

### Post by urkitarke on 2011-02-09
Hi
I have the same problem but i don´t know how solved it.

Can you explain me???

thanks

---

