---
title: "Matlab's Latex interpreter: broken fonts in EPS and PDF"
date: 2011-05-27
forum: General Help
---

### Post by fyslab on 2011-05-27
Our Matlab users met the problem in Ubuntu while using Latex interpreter in Matlab. Namely, eps and pdf files generation out of Matlab plot outputs plot legend and axes lables incorrectly. All the letters are mixed, impression that character spaces are too dense.

We can't blame Matlab, since exactly the same examples with the same Matlab version work fine on CentOS.

We tested Ubntu 9.10, 10.4 and 10.10 -- same problem. Matlab version R2010b.

In addition, jpg, png generated with no problems. It's eps and pdf only 

Matlab example:
plot(1:1:10)
xlabel('example','Interpreter','latex')
ylabel('ExAmPlE','Interpreter','latex')
a=legend('EXAMPLE example ExAmPle')
set(a,'Interpreter','latex','Fontsize',13)
print -depsc2  figure1

I am attaching a PDF, looks same as eps, but easier to display.

Any hint is welcome.

---

### Post by fyslab on 2011-05-27
In addition, in Matlab's own .fig files, Latex special characters looks incorrecly. Also, Ubuntu only problem.

---

### Post by fyslab on 2011-05-27
What we have tried already.

Add Matlab's fonts to font cash (Matlab is on shared NFS disk)
 $ sudo ln -s *$MATLAB/sys/fonts/ttf/cm/*  */usr/share/fonts/* 
 $ sudo fc-cache -f -v 

No results.

Removing extra Latex fonts did not help either:
  $ sudo apt-get --purge remove latex-xft-fonts 

Removing 'compiz' packages did not help.

---

### Post by fyslab on 2011-05-30
Anyone experienced with Matlab Latex interpreter?

---

### Post by hawthornso23 on 2011-05-30
Maybe something to do with missing tfm (font metric) files?

---

### Post by Topsiho on 2011-05-30
I have no experience with Matlab, though I have dabbled somewhat with the open source clone Octave of Matlab. I have no experience witk LaTeX, though I think maybe you are missing one of the available latex files, to be found in Synaptic, such as latex-xft-fonts. But you'd better look yourself :)

I write this especially to put your attention and that of the readers to the open source clone Octave. It costs less, and it is a very close clone. And as it's backed by a number of american universities, I guess it is good.

Topsiho

---

### Post by hawthornso23 on 2011-05-30
That is a +1 from me on octave. The beauty of it is that as it is GPL you can even put it on a CD and hand it out to all your students. No mucking around with license servers. And of course it is free, whereas MATLAB is ... ahem ... very much NOT free. And since octave is in the repositories, installing it is easy and all the dependencies (like tfm files) get taken care of for you.

---

### Post by 3Miro on 2011-05-30
Last time I checked, Octave didn't have a fraction of the plotting tools that MATLAB does. Unfortunately, Octave is not a viable alternative for serious work.

In my experience, MATLAB + LaTeX = disaster.

Here is some MATLAB code that works for me, although I am not sure why. You can try installing the Liberation forts for Ubuntu (it may help). You can also try to install ubuntu-restricted-extras, it comes with some ms ttf fonts.

```

set(get(gcf,'CurrentAxes'),'FontSize',18,'FontName','Liberation')
xlabel('$x$','FontName','Liberation','FontSize',34,'Interpreter','latex');
        ylabel(['$\Delta u^{(',num2str(alpha),',1000)}(x;\omega)$'],'FontName','Liberation','FontSize',34,'Interpreter','latex');

```

---

### Post by Topsiho on 2011-05-30
I am not sure when was the last time you checked Octave, and what serious work you do with Matlab (or would like to do using Octave). If that is only plotting, you could probably better try Gnuplot.

I think that one can do some plotting in Octave, how this compares to Matlab I don't know. (last time I checked Matlab was, eh, probably some 15 to 20 years ago :) ). As Octave, according to it's manual (3.0.1), pg 213, interacts with Gnuplot, I don't think you can state seriously that Octave can not be used for serious plotting work.

But I must say that I am thinking of students, who use Matlab or Octave not only for plotting work, at least they should consider how to use the other possibilities, and explore Mathematics that way.

You also say: "In my experience, MATLAB + LaTeX = disaster". This is opposite to what the original poster states, he says only in Ubuntu this doesn't work, which I very much deplore, as Ubuntero.

Howgh,

Topsiho

---

### Post by 3Miro on 2011-05-30
> **Topsiho said:**
> I am not sure when was the last time you checked Octave, and what serious work you do with Matlab (or would like to do using Octave). If that is only plotting, you could probably better try Gnuplot.

I think that one can do some plotting in Octave, how this compares to Matlab I don't know. (last time I checked Matlab was, eh, probably some 15 to 20 years ago :) ). As Octave, according to it's manual (3.0.1), pg 213, interacts with Gnuplot, I don't think you can state seriously that Octave can not be used for serious plotting work.

But I must say that I am thinking of students, who use Matlab or Octave not only for plotting work, at least they should consider how to use the other possibilities, and explore Mathematics that way.

You also say: "In my experience, MATLAB + LaTeX = disaster". This is opposite to what the original poster states, he says only in Ubuntu this doesn't work, which I very much deplore, as Ubuntero.

Howgh,

Topsiho

It has been some time since I have taken in depth look at Octave, so here are some questions:

- It used to be very hard to make your own .m function files, I couldn't even figure out how to call them. Can you call them with a simple function_name( params ) yet?
- Sparse matrices used different formats (different from MATLAB) meaning that the code is not compatible. Is that still the case?
- Can you do LaTeX in Gnu Plot/Octave? I just installed Octave in a VirtualBox and it doesn't recognize the LaTeX commands.
- Can I get a plot picture from Octave and directly export it into an .eps file to add to a paper that I am writing? I am sure that GnuPlot can do that, but can it be done with  Octave + GnuPlot interaction.

The OP tested LaTeX + MATLAB on CentOS and Ubuntu. I have tested it on Arch and Gentoo (can't remember if I did Fedora or not). Even if you get the interpreter to work correctly, you still get in trouble with having to fiddle with things quite a bit to get them to work correctly (especially when you have to export the picture to .eps). I don't think this is an Ubuntu problem, I think it is a general problem with MATLAB.

---

### Post by fyslab on 2011-05-30
Octave vs. Matlab is not in question here. Some of us do use Octave, but since we have access to University licences we also run Matlab.

Recently we migrated from CentOS to Ubuntu and Matlab Latex interpreter thing is one of the issues that we are trying to solve. We need to get everything working with Ubuntu that used to work in CentOS.

---

### Post by fyslab on 2011-05-30
Matlab's latex interpreter will use Computer Modern fonts independently on what family font one has defined for the axis labels and legend.

Latex's fonts comes among 'texlive' packages. We have all of them installed by default. In particular those cm*.tfm are in /usr/share/texmf-texlive/fonts/tfm/

$ xlsfonts | grep cmr
-tex-cmr10-medium-r-normal--0-0-0-0-p-0-fontspecific-0
-unknown-cmr10-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific
-unknown-cmr12-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific
-unknown-cmr17-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific
-unknown-cmr5-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific
-unknown-cmr6-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific
-unknown-cmr7-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific
-unknown-cmr8-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific
-unknown-cmr9-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific
$ find /usr/share/texmf-texlive/fonts/ -name 'cmr*.tfm'
/usr/share/texmf-texlive/fonts/tfm/public/figbas/cmrj.tfm
/usr/share/texmf-texlive/fonts/tfm/public/cm/cmr17.tfm
/usr/share/texmf-texlive/fonts/tfm/public/cm/cmr5.tfm
/usr/share/texmf-texlive/fonts/tfm/public/cm/cmr8.tfm
/usr/share/texmf-texlive/fonts/tfm/public/cm/cmr9.tfm
/usr/share/texmf-texlive/fonts/tfm/public/cm/cmr10.tfm
/usr/share/texmf-texlive/fonts/tfm/public/cm/cmr7.tfm
/usr/share/texmf-texlive/fonts/tfm/public/cm/cmr6.tfm
/usr/share/texmf-texlive/fonts/tfm/public/cm/cmr12.tfm

---

### Post by Topsiho on 2011-05-30
Maybe this can help, found googling using Octave .eps:

[http://www.math.tamu.edu/~comech/tools/octave-basics/](http://www.math.tamu.edu/~comech/tools/octave-basics/)

Topsiho

---

### Post by fyslab on 2011-05-30
Thanks for the link, but not much help, basic hints about printing to EPS.

In our case we either miss some font  or have them missconfigured. Though we tried already rebuild and add everything what we could.

Though not everything, since the problem is yet there.

---

### Post by fyslab on 2011-05-31
Latex in Matlab used to have problem with rendering special characters, and people claim the 'latex-xft-fonts' package:
[http://www.mathworks.com/matlabcentral/newsreader/view_thread/258809](http://www.mathworks.com/matlabcentral/newsreader/view_thread/258809)

In our case removing this package / restaritng GDM didn't help. People also say that the problem is in GDM only, KDE should work fine. This we can't confirm, since no KDE.

---

### Post by hawthornso23 on 2011-06-01
I can't directly help with your problem as the system I use MATlab on isn't my ubuntu system.
But I've been thinking about it and doing a little background reading. 

It appears that the default font for axes in MATlab isn't a latex font - it is Helvetica! Helvetica isn't included in MATlab. MATlab expects to find it on the system. This is a terrible choice of default! Helvetica is a very old font beset by technical and legal problems. You won't find it on ubuntu for those reasons. You won't even find it on a Windows machine these days. Looks like the owners of the font started getting a bit greedy even for Microsoft. Getting this font onto ubuntu MIGHT fix your problem but looks to be a total hassle. To be legal about it you'd have to buy the font.

On the other hand there are many Helvetica equivalent fonts which even an expert can't tell apart from the original. Ubuntu includes several. The Microsoft Ariel font is one and is available free as in beer via the microsoft free font package in restricted extras. The liberation fonts are also Helvetica equivalents and these are free in all senses of the word.
It looks to me like telling MATlab to use one of these fonts instead might be the answer.

[http://www.mathworks.com/support/solutions/en/data/1-12NHPX/index.html?product=ML&solution=1-12NHPX](http://www.mathworks.com/support/solutions/en/data/1-12NHPX/index.html?product=ML&solution=1-12NHPX)

Good Luck!

---

### Post by fyslab on 2011-06-06
I believe Helvetica is not a problem either. The resulting postscript file analysis shows that if in Matlab one uses Tex instead Latex as an interpreter the output EPS / PDF graphs come out fully ok, and pure Tex uses Helvetica only, while Latex uses a mix of Helvetica and Computer Modern. Only the later is problematic.

In Ubuntu 10.04 we have a set of Adobe fonts including Helvetica.

---

### Post by hennessy.matt on 2011-06-08
I had the exact same problem in my last Ubuntu installation (which was 10.04 and Matlab r2008a) and although I was able to fix it, I have since forgotten how! Now I face the problem again because I've upgraded to Ubuntu 11.04. Anyway, I'll play around and post a solution if I come across one.

---

### Post by fyslab on 2011-06-10
Any hint is warmly welcome. The problem is still there.

---

### Post by fyslab on 2011-07-21
This is what we got from Mathworks by now.  About to test fresh install without Lyx.

------------------------------------------------

On 2011-07-20 17:42, support at mathworks.co.uk wrote:
> >
>  > I have been unable to reproduce this issue by installing other  font packages (except for ttf-lyx and latex-xft-fonts). My  recommendation at this point is to try installing Ubuntu from the disk.  If this works, try installing each of the packages from the old  distribution except for ttf-lyx and latex-xtf-fonts.
> >
>  > The alternative is to switch to the 'tex' editor, or reduce the  font size property to around 8. I suspect the issue is that MATLAB isn't  able to render this font correctly under certain conditions, while the  print mechanics still can. This causes a mismatch of boundary box and  size of actual text, which causes the unusual character spacing. This  problem is known to our developers, I have attached the information here  to the bug report regarding this problem.
> >
> > I  will now close this service request. However, if this problem persists  when doing the recommended steps above; I am happy to reopen this case  or create a new service request to investigate into those details  further.

---

### Post by fyslab on 2011-07-21
If there are same kind of fonts from two packages, is there a way to set priorities, stress that this font, from this directory must be used instead of any other?

Is it possible at user level without root privileges?

I am asking since we would like to keep both and Lyx and Matlab and have them both running on the same Ubuntu machine.

---

### Post by fyslab on 2011-07-28
The problem is solved. Solution:
* remove ttf-lyx and latex-xft-fonts
* make sure that Matlab fonts are in cache

$ sudo aptitude remove latex-xft-fonts
$ sudo aptitude remove ttf-lyx

Either add Matlab fonts dir to your /etc/fonts/fonts.conf 'Font directory list' or make a link to already included directory and rebuild the cache
$ sudo ln -s *$MATLAB/sys/fonts/ttf/cm/*  */usr/share/fonts/* 
 $ sudo fc-cache -f -v

If no root privileges, one can try linking to ~/.fonts in your home.

I also checked Lyx, it seems to work fine without those font packages.

---

### Post by Topsiho on 2011-07-28
Real great that you post your solution here :)
Wish everyone did that, so others can use the solution.

You should mark this thread as solved. I have no experience how to do this, probably there is an option for the OP in Thread Tools in the top of this page. As I am not the OP probably that's why I don't see such an option :)

Greetings from Topsiho

---

### Post by fyslab on 2011-08-01
Sorry, not solved yet. Not everyone was happy about removing ttf-lyx since it has automagically removed python-matplotlib packages.

Now we still have to find out how to get ttf-lyx and Matlab to work together :(

Any idea?

---

### Post by totoxa on 2012-08-30
I have the same problem in Ubuntu 10.04, MATLAB 2008b and TeXlive vanilla, it was working fine the last time i used matlab, and today i run a old code and the text was displayed bad. i have only updated texlive and installed the ubuntu updates..

---

