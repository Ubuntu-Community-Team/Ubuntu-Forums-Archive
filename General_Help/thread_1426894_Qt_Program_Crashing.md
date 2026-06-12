---
title: "Qt Program Crashing"
date: 2010-03-10
forum: General Help
---

### Post by Josh61980 on 2010-03-10
Hey All,
I've been teaching myself Qt however the program I'm working on keeps crashing and I'm not sure why. I'm not sure if this is the right place to ask but I'd thought I'd give it a go.

First off my tools
Qt 4.5.2
Qt Desginer 4.5.2
gcc 4.4.1
qmake 2.01a
make 3.81

Second off the error I'm getting.
```
Program received signal SIGSEGV, Segmentation fault.
0x00b6066f in QString::toLatin1() const () from /usr/lib/libQtCore.so.4
```

It looks like it's crashing out on this line

```
cout << "Name: "<<pCurrent->sName.toStdString()<<endl;
```

pCurrent is a pointer to a class I made called Player here is the definition
```
class Player
{
public:
	QString sName;
	int iTick;

	//functions
	Player(QString s, int i);
	bool operator<(const Player &p);
};
#endif
```

here is the line where pCurrent gets initialised 

```
	pCurrent = &lCombantants.front();
```

here is the line where lCombantants is a linked list and the element is added here.
```
	lCombantants.push_back(Player(lneName->text(),tick));
```

Syntactically it looks fine I'm not sure why it's crashing.  Also if it helps the line above it

```
cout << "iTick: "<<pCurrent->iTick<<endl;
```

runs fine so the pointer itself is set up right it seems to me to be a problem with the QString object somehow.  Any help would be appropriated, thank you.

---

