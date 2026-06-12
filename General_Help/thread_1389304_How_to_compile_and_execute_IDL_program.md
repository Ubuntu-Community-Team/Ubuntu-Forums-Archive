---
title: "How to compile and execute IDL program???"
date: 2010-01-24
forum: General Help
---

### Post by sundar_ima on 2010-01-24
following is the IDL program found on the internet but i dont know how to compile and execute (even dont know can it be done under linux). Can anybody help me out???

```
;    Tephigram Atmospheric Thermodynamic Diagram
; The axes are temperature and theta (theta=potential temperature) 
; (actually it should be log(theta)).
; The axes are rotated by 45 degrees so the isobars are nearly horizontal.

;
; A sounding may optionally be plotted on the diagram. 
; The sounding format is three header lines, then each line has:
;    pressure (mb), temperature (C), dew point (C)
;
; Program in IDL      October 1997

; Frank Evans  University of Colorado    evans@nit.colorado.edu



output = 'ps'    ; 'x' for X-windows, 'ps' for Postscript file
outfile='tephigram.ps'

soundfile=''
plottitle='Tephigram'
;outfile='tephi_den97093012.ps'
;soundfile='den97093012.snd'
;plottitle='Denver 97-09-30 12Z'



if output eq 'ps' then begin
  set_plot, 'ps'
  device, filename=outfile, /portrait, /times, $
        ysize=25.0, xsize=20.0, yoffset=1.0, xoffset=0.7
  !p.font = -3
endif else begin

  set_plot, 'x' 
  window, xsize=600, ysize=800, title='T-phi gram'
  !p.font = -3
endelse


;  Set up plot area
xlo=0.07  &  ylo=0.1  &  xhi=0.87  &  yhi=0.95
plot, [0], [0], position=[xlo,ylo,xhi,yhi], /nodata, ticklen=0.0, $

	xticks=1, xtickname=[' ',' '], yticks=1, ytickname=[' ',' '], $
	title='!5'+plottitle+'!3', charsize=1.5, thick=1.5
!x.s = [0.,1.]
!y.s = [0.,1.]

;  Set up IDL scaling and rotation transformation matrix

T1=-10  &  T2=40  &  theta1=-12
scale=(xhi-xlo)*sqrt(0.5)/(T2-T1)
t3d, /reset, translate=-[T1,theta1,0.], scale=[scale,scale,1.]
t3d, rotate=[0,0,-45]
t3d, scale=[1.0,0.75,1.]
t3d, translate=[xlo,ylo,0.]


;  Initialize constants that control where lines drawn and labeled
thetalo=-20.     &  thetahi=110.
Tlo=-90.         &  Thi=40.
Tstart=-70.      &  Tend=+30.         &  Tstep=10.
Tstartlab=-60.   &  Tendlab=+30.      &  thetalabel=30.

thetastart=-30.  &  thetaend=+90.     &  thetastep=10.
thetastartlab=0. &  thetaendlab=+80.  &  Tlabel=-20.      
Pstart=1000.     &  Pend=200.         &  Pstep=-100.




;  Make the temperature lines and label them

for T = Tstart, Tend, Tstep do begin
    plots, [T,T], [thetalo,thetahi], /t3d,  noclip=0, thick=1.5
endfor
for T = Tstartlab, Tendlab, Tstep do begin
    xyouts, T-0.5,thetalabel, /t3d, alignment=-0.3, orient=90, noclip=0, $

	size=150, charthick=1.5, 'T='+string(T,format='(I3)'), /data
endfor


;  Make the theta (potential temperature) lines and label them
for theta = thetastart, thetaend, thetastep do begin

    plots, [Tlo,Thi], [theta,theta], /t3d,  noclip=0, thick=1.5
endfor
for theta = thetastartlab, thetaendlab, thetastep do begin
    xyouts, Tlabel, theta+0.5, alignment=-0.1, orient=0, noclip=0,  $
	size=150, charthick=1.5, /t3d, '!7h!3='+string(theta,format='(I2)')

endfor



; Make the curves of constant pressure 
; Use theta = T*(1000/p)^0.286
Tarr=Tlo+(Thi-Tlo)*findgen(100)/100.0
for P = Pstart, Pend, Pstep do begin
    thetaarr = -273.2 + (273.2+Tarr)*(1000/P)^0.286

    plots, Tarr, thetaarr, /t3d, noclip=0, linestyle=2
    x = (P/1000)^0.286  &  delT = (273+T2)*(1-x)/(1+x) 
    T = T2 - delT  &    theta = T2 + delT
    xyouts, T, theta, alignment=0.1, orient=53.13,  $

	size=150, charthick=1.5, /t3d, string(P,format='(I4)')
endfor
xyouts, xhi+0.06, ylo-0.01, alignment=0.5,  $
	size=1.5, charthick=1.5, '!5p (mb)!3', /normal



;  Make the saturated specific humidity curves

;    q_s = 0.622*e_s/p
qs=[30,20,15,10,7,5,3,2,1.5,1.0,0.7]
Tarr=-40+findgen(75)
for i = 0, n_elements(qs)-1 do begin
    Tk=Tarr+273.2
    es = exp( -6763.6/Tk - 4.9283*alog(Tk) + 54.2190 )
    Pqs = 0.622*es/(0.001*qs(i))

    thetaarr = -273.2 + (273.2+Tarr)*(1000/Pqs)^0.286
    plots, Tarr, thetaarr, /t3d, noclip=0, linestyle=1
endfor
Pqs=[1070,1070,1070,1070,1070,1070,1070,1070,970,800,695]
Tarr=[33,26,21,15,9,4,-3,-8,-15,-22,-27]

thetaarr = -273.2 + (273.2+Tarr)*(1000.0/Pqs)^0.286
xyouts, Tarr, thetaarr, alignment=0.0, orient=53,  $
 	size=120, charthick=1.5, /t3d, string(qs,format='(F4.1)')
xyouts, xlo, ylo-0.05, alignment=0.0,  $

	size=1.5, charthick=1.5, '!5q!Ds!N (g/kg)!3', /normal




;  Make the saturated adiabat curves
;    Use dtheta = -L*theta/(Cp*T) dqs and integrate from T=-40 C
Tarr=fltarr(70)  &  thetaarr=fltarr(70)

for theta = thetastartlab, thetaend, thetastep do begin
   T = -40
   P = 1000*( (T+273.2)/(theta+273.2) )^3.5 
   Tk=T+273.2
   es = exp( -6763.6/Tk - 4.9283*alog(Tk) + 54.2190 )
   qs0 = 0.622*es/P
   thetaarr(0) = theta

   Tarr(0) = T
   for i = 1, 70-1 do begin
     T = T + 1.0
     P = 1000*( (T+273.2)/(thetaarr(i-1)+273.2) )^3.5 
     Tk=T+273.2
     es = exp( -6763.6/Tk - 4.9283*alog(Tk) + 54.2190 )
     qs = 0.622*es/P

     thetaarr(i) = thetaarr(i-1) - $
          (2.5E6/1004)* (273.2+thetaarr(i-1))/(273.2+T) * (qs-qs0)
     qs0 = qs                
     Tarr(i) = T
   endfor
   plots, Tarr, thetaarr, /t3d, noclip=0, linestyle=5

endfor


!p.charthick=1.5
!p.charsize=1.2
plots, [0.25,0.30], [0.04,0.04], /normal, linestyle=2
xyouts, 0.31, 0.04, alignment=0.0,  '!5isobars (pressure)', /normal
plots, [0.25,0.30], [0.02,0.02], /normal, linestyle=5

xyouts, 0.31, 0.02, alignment=0.0,  '!5saturated adiabats', /normal
plots, [0.55,0.60], [0.04,0.04], /normal, linestyle=1
xyouts, 0.61, 0.04, alignment=0.0,  '!5sat. specific humidity', /normal
plots, [0.55,0.60], [0.02,0.02], /normal, linestyle=0

xyouts, 0.61, 0.02, alignment=0.0,  '!5dry adiabats (!7h!5)', /normal



;  Sounding file format: pressure (mb), temperature (C), dew point (C)

if (soundfile ne '') then begin
  MAXLEV=100

  pres=fltarr(MAXLEV)
  temp=fltarr(MAXLEV)
  dewpt=fltarr(MAXLEV)
  ; Read in the atmospheric sounding profile
  openr,1, soundfile
  junk=strarr(3)
  readf,1, junk       ; Skip header lines
  i = 0

  while not EOF(1) do begin        ; Read in however many levels there are
    readf,1, p, t, td
    pres(i) = p
    temp(i) = t
    dewpt(i) = td
    i = i + 1
  endwhile
  close,1
  nlev = i-1

  pres=pres(0:nlev-1)
  temp=temp(0:nlev-1)
  dewpt=dewpt(0:nlev-1)
;   Plot the temperature profile
  thetaarr = -273.2 + (273.2+temp)*(1000/pres)^0.286
  plots, temp, thetaarr, /t3d, noclip=0, linestyle=0, thick=3

;   Plot the dewpoint temperature profile
  thetaarr = -273.2 + (273.2+dewpt)*(1000/pres)^0.286
  plots, dewpt, thetaarr, /t3d, noclip=0, linestyle=0, thick=3
endif


if output eq 'ps' then device, /close


end

```

---

### Post by sundar_ima on 2010-01-25
Is there anyone to help me out?

---

### Post by houseworkshy on 2010-01-25
Hello Monty. Bump

---

### Post by houseworkshy on 2010-01-25
Just realised that that is python.  Well it looks like python but I'm not sure about the white spaces, I've only just started learning it and so far it has been white spaces in groups of four, some of those look like three.  No problem.  Just install the appropriate idle.  Make sure it is for the same python version as the program.  Also make sure you have whichever python it is for. Run the idle, open a new window.  Then paste it into the idle window. Run module, save when it asks, and that should be it.

The horses mouth
[http://www.python.org](http://www.python.org)
Lots of good documentation and resources here

---

### Post by Onesimus on 2010-01-25
> **sundar_ima said:**
> following is the IDL program found on the internet but i dont know how to compile and execute (even dont know can it be done under linux). Can anybody help me out???


I am presuming that you have purchased a IDL licence for Linux ([http://www.ittvis.com/ProductServices/IDL.aspx]("http://www.ittvis.com/ProductServices/IDL.aspx"))

Then compiling code should be in their help sections.

This website ([http://www.dfanning.com/]("http://www.dfanning.com/")) is a wealth of info about IDL

---

### Post by Onesimus on 2010-01-25
> **houseworkshy said:**
> Just realised that that is python.  Well it looks like python 

It is not python, but IDL  (Interactive Data Language) designed for analysing scientific data. See Wiki page ([http://en.wikipedia.org/wiki/IDL_%28programming_language%29]("http://en.wikipedia.org/wiki/IDL_%28programming_language%29"))

---

### Post by houseworkshy on 2010-01-25
Thanks Onesimus.  I suppose one should never post after an all nighter.  Wrong language altogether, woops.  Appologies to all...think I'd better log out and get some sleep now.

---

### Post by sundar_ima on 2010-01-26
It seems IDL progarm need license. But there is an alternative for GNU Linux "GDL " [http://gnudatalanguage.sourceforge.net/]("http://gnudatalanguage.sourceforge.net/"). The web page says IDL programs can be executed on GDL. I have no clue how to do that. Please go through the page and if you can understand something then let me know.

---

### Post by t4thfavor on 2010-01-26
It looks pretty simple, go and port it to gdl, or python, or some other language. 

I was going to say python as well.

EDIT: 
Upon secondary review, I am an idiot. It's not that simple :)

---

### Post by lusepuster on 2010-05-17
IDL is a closed, proprietary language, but the free GDL/GnuDataLanguage implementation is decent and very complete in its computational modules. Unfortunately, not so complete in its data visualization modules.

My advice would be; install GDL (the gnudatalanguage package); navigate to the folder where you put the file with the program you downloaded. Open GDL by typing "gdl" in your shell. You will now enter gdl and be greeted by a prompt looking something like "gdl>". Type ".r programname.pro", hit enter, and it will tell you something like "Compiled MODULNAME". You can now run the program, it might just be by typing "MODULENAME" - or, if it requires an input file, it'll be something like "MODULENAME, input_file_name.ext".

It might or might not work, depending on which IDL features it requires. Good luck.

EDIT: At closer look, the syntax of the file looks a bit odd. You might need to add an opening line saying "pro WHATEVER_YOU_WANT_TO_CALL_THE_ROUTINE " in the beginning of the file (before or after the initial comments doesn't matter).

---

### Post by sundar_ima on 2010-05-17
**@ lusepuster**

Thank you for your kind reply. Here is the error message i got while trying to run the program. I saved the program as tephi.pro

```
sundar@sundar-laptop:~/Desktop$ gdl
GDL - GNU Data Language, Version 0.9
For basic information type HELP,/INFO
'GDL_STARTUP'/'IDL_STARTUP' environment variables both not set.
No startup file read.
GDL> r tephi.pro 
Parser syntax error: unexpected token: TEPHI
% Parser syntax error: unexpected token: TEPHI
```

---

### Post by sundar_ima on 2010-05-17
After reading your post carefully i tried it again and got the following error message...

```
GDL> .r tephi.pro
% Compiled module: WHATEVER_YOU_WANT_TO_CALL_THE_ROUTINE.
GDL> MODULENAME
Procedure not found: MODULENAME
% Procedure not found: MODULENAME
% Execution halted at: $MAIN$          
GDL> WHATEVER_YOU_WANT_TO_CALL_THE_ROUTINE
Keyword parameter TIMES not allowed in call to: DEVICE
% Keyword parameter TIMES not allowed in call to: DEVICE
% Execution halted at: WHATEVER_YOU_WANT_TO_CALL_THE_ROUTINE    30 tephi.pro
%                      $MAIN$          
GDL> WHATEVER_YOU_WANT_TO_CALL_THE_ROUTINE, tephi.pro 
Parser syntax error: unexpected token: TEPHI
% Parser syntax error: unexpected token: TEPHI
GDL> WHATEVER_YOU_WANT_TO_CALL_THE_ROUTINE, tephi.ext
Variable is undefined: TEPHI
% Variable is undefined: TEPHI
% Execution halted at: WHATEVER_YOU_WANT_TO_CALL_THE_ROUTINE     1 tephi.pro
%                      $MAIN$          
GDL> 

```

---

