---
title: "College Student Struggling with Java"
date: 2011-01-12
forum: General Help
---

### Post by JustinOkay on 2011-01-12
I'm a freshman in at Highline Community College and I'm taking a java class this quarter.  I'm trying to create and simulate a simple 4 way intersection using lines and GTurtle. So far my code is pretty basic and incomplete. My goal is to make my murtle object turn left at the stop. I was wondering if someone could just set me straight or maybe offer some tips to help me out. Here's my code.

import acm.graphics.*;
import acm.program.*;
import java.awt.*;

public class MurtleDraws extends GraphicsProgram
{

public void init()
{
    setSize(750,600);
    setBackground(java.awt.Color.orange);
}

public void run()
{



//Four way intersection grid
    GTurtle murtle = new GTurtle();
    add(murtle);
    murtle.penDown();

    murtle.setLocation(0,400);
    murtle.forward(300);
    murtle.right(90);
    murtle.forward(300);

    murtle.setLocation(300,0);
    murtle.forward(275);
    murtle.right(90);
    murtle.forward(300);

    murtle.setLocation(450,275);
    murtle.right(90);
    murtle.forward(300);
    murtle.setLocation(450,275);
    murtle.right(90);
    murtle.forward(300);

    murtle.setLocation(450,400);
    murtle.forward(300);
    murtle.setLocation(450,400);
    murtle.right(90);
    murtle.forward(300);

//Road dash marks
    murtle.setLocation(0,340);
    murtle.left(90);
    murtle.forward(20);
    murtle.setLocation(40,340);
    murtle.forward(20);
    murtle.setLocation(80,340);
    murtle.forward(20);
    murtle.setLocation(120,340);
    murtle.forward(20);
    murtle.setLocation(160,340);
    murtle.forward(20);
    murtle.setLocation(200,340);
    murtle.forward(20);
    murtle.setLocation(240,340);
    murtle.forward(20);
    murtle.setLocation(280,340);
    murtle.forward(20);

    murtle.setLocation(470,340);
    murtle.forward(20);
    murtle.setLocation(510,340);
    murtle.forward(20);
    murtle.setLocation(550,340);
    murtle.forward(20);
    murtle.setLocation(590,340);
    murtle.forward(20);
    murtle.setLocation(630,340);
    murtle.forward(20);
    murtle.setLocation(670,340);
    murtle.forward(20);
    murtle.setLocation(710,340);
    murtle.forward(20);
    murtle.setLocation(750,340);
    murtle.forward(20);
    murtle.setLocation(780,340);

    murtle.setLocation(375,0);
    murtle.right(90);
    murtle.forward(20);
    murtle.setLocation(375,40);
    murtle.forward(20);
    murtle.setLocation(375,80);
    murtle.forward(20);
    murtle.setLocation(375,120);
    murtle.forward(20);
    murtle.setLocation(375,160);
    murtle.forward(20);
    murtle.setLocation(375,200);
    murtle.forward(20);
    murtle.setLocation(375,240);
    murtle.forward(20);

    murtle.setLocation(375,415);
    murtle.forward(20);
    murtle.setLocation(375,455);
    murtle.forward(20);
    murtle.setLocation(375,495);
    murtle.forward(20);
    murtle.setLocation(375,535);
    murtle.forward(20);
    murtle.setLocation(375,575);
    murtle.forward(20);
    murtle.setLocation(375,615);

//Stop Sign - Having problems moving octagon above the stick. Also trying to make stop sign red
    murtle.setLocation(500,450);
    murtle.right(180);
    murtle.forward(100);
    murtle.setLocation(520,450);
    murtle.forward(100);
    murtle.setLocation(500,450);
    murtle.right(90);
    murtle.forward(20);
    murtle.setLocation(500,350);
    murtle.forward(20);

    murtle.setLocation(500,350);
    murtle.right(90);
    murtle.forward(25);
    murtle.right(45);
    murtle.forward(25);
    murtle.right(45);
    murtle.forward(25);
    murtle.right(45);
    murtle.forward(25);
    murtle.right(45);
    murtle.forward(25);
    murtle.right(45);
    murtle.forward(25);
    murtle.right(45);
    murtle.forward(25);
    murtle.right(45);
    murtle.forward(25);
    murtle.right(45);
    murtle.forward(25);
    murtle.right(180);

//MurtleTheCar - HOW DO I HIDE THE PEN?

    murtle.setLocation(420,600);
    murtle.forward(175);

    








}


}

---

### Post by TeoBigusGeekus on 2011-01-12
I don't know java, but you might get luckier in the [Programming Talk Forum]("http://ubuntuforums.org/forumdisplay.php?f=39").

---

