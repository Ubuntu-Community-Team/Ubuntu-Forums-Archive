---
title: "Qt: Creating a Window errors."
date: 2011-07-30
forum: General Help
---

### Post by samvkampen on 2011-07-30
[SIZE=2][FONT=Verdana]Hi everyone. Because I am a beginning programmer, I wanted to look at the Linux side of programming. Starting, I wanted to create a simple window, with information inside ('text area' element in Visual C/C++)[/FONT][/SIZE] [SIZE=2][FONT=Verdana]with Qt ([http://qt.nokia.com](http://qt.nokia.com)). I used Qt because of a forum post, saying Qt could be used, with the following code:

[/FONT][/SIZE]```
#include <QApplication> 
    #include <QFont> 
    #include <QPushButton> 
 
    int main(int argc, char *argv[]) 
    { 
        QApplication app(argc, argv); 
 
        QPushButton quit("Quit"); 
        quit.resize(75, 30); 
        quit.setFont(QFont("Times", 18, QFont::Bold)); 
 
        QObject::connect(&quit, SIGNAL(clicked()), &app, SLOT(quit())); 
 
        quit.show(); 
        return app.exec(); 
    } 
 
```[FONT=Verdana][SIZE=2], but that became this error when compiled (in Code::Blocks):

[/SIZE][/FONT]sh: /home/sam/QtWindowAPp: permission denied
process returned 126 (0x7E)

[FONT=Verdana][SIZE=2]That's what I get, could anyone help?
Thanks in advance,
Sam
[/SIZE][/FONT]

---

