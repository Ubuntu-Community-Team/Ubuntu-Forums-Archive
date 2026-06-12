---
title: "Problem with running an applet."
date: 2011-01-13
forum: General Help
---

### Post by leecourt on 2011-01-13
Hey I'm new to these forums, and I have a slight problem with an applet I'm trying to run. I don't have problems running any other java applets from other websites or anything but for some reason the applet I developed shows the gray-screen and says 'Start: applet not initialized.' at the bottom.

There are no errors in the error console.

Java is working on my web browser (mozilla firefox).

I'm running Ubuntu 10.10.

Here's my code, the program is for my friend and she uses a mac, so is this issue specific for Ubuntu? I made the applet using Eclipse Ganymede.

```
import java.awt.*;
import java.applet.*;

public class JaneApplet extends Applet{
    
    private static final long serialVersionUID = 1L;
    int width, height;
    AudioClip s;
    
    public void init(){
        
        s = getAudioClip(getCodeBase(), "I Can Change2.wav");
        width = getSize().width;
        height = getSize().height;
        setBackground( Color.black );
        s.loop();
    }
    
    public void paint(Graphics g){

        //format randomized colors
        int red = (int)( Math.random() * 256 );
        int green = (int)( Math.random() * 256 );
        int blue = (int)( Math.random() * 256 );
        
        //format randomized colors2
        int red2 = (int)( Math.random() * 256 );
        int green2 = (int)( Math.random() * 256 );
        int blue2 = (int)( Math.random() * 256 );
        
        //format randomized colors3
        int red3 = (int)( Math.random() * 256 );
        int green3 = (int)( Math.random() * 256 );
        int blue3 = (int)( Math.random() * 256 );
        
        //set random color
        g.setColor( Color.magenta );
        
        g.drawString("<3   HALEY   <3", width / 4, height - 35);
        
        for( int i = 0; i < 5; ++i ){
            
            //top lines
            g.setColor( new Color( red, green, blue ));
            g.drawLine( width, height / 3, (i + 3) * width / 10, 0 );
            g.drawLine( 0, height / 3, (i + 3) * width / 10, 0 );
            
            //different color for the bottom lines
            g.setColor( new Color( red2, green2, blue2 ));
            g.drawLine( 0, height, width, i * (height - 350) );
            g.drawLine( width, height, 0, i * (height - 350) );
            
            //random boxes, diff colors, random numbers
            g.setColor( new Color( red3, green3, blue3));
            g.draw3DRect( green3, red3, blue3, blue2, true);
            g.drawString( Integer.toString(red), (width / 4), height - 20 );
            g.drawString( Integer.toString(blue), (width / 4) + 40, height - 20 );
            g.drawString( Integer.toString(green), (width / 4) + 80, height - 20 );
        }
    
            repaint();
    }
}
```As you can see it's very simple, along with the HTML code:

```

<HTML>
<HEAD>
<TITLE>ALEXANDER & JANE</TITLE>
</HEAD><BODY>
<APPLET CODE = "./JaneApplet.class" WIDTH = 400 HEIGHT = 400 ></APPLET>
</BODY>
</HTML>
```The .class file, .au song, and .html file are all in the same directory.

Thanks, any support would be very helpful!

---

### Post by cmoraes on 2011-01-13
Try setting your CLASSPATH to include your current directory.

---

### Post by leecourt on 2011-01-13
Hmm, eclipse and other IDE's automatically assume file paths; the applet compiles neatly in eclipse and there are no errors. 


I'm guessing it has something to do with a java plugin or something.

---

