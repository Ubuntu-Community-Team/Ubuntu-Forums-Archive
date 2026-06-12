---
title: "C++, qt4 graphics and putpixle"
date: 2011-04-29
forum: General Help
---

### Post by machdohvah on 2011-04-29
OK... So I am trying to write a program that will read a file with each byte representing a colour from "0" to "F", and then using a putpixle function to display a dot in that colour on the screen (or window for that matter). As the dots line up properly, using the end-of-line in the file to start the next line, the entire contents of the file is then displayed. But, this was created in DOS years ago by me and I would like to know how to create a putpixle function using the "qt4" libraries.

```
// DECKSHOW.CPP 
 
#include <conio.h> 
#include <graphics.h> 
#include <stdlib.h> 
#include <stdio.h> 
#include <string.h> 
 
#define ESC 0x1b 
#define PATH_TO_BGI "\\TC\\BGI" 
#define PATH_TO_CARDS "\\MYDOCS\\TC\\CARDS\\PXL\\" 
 
void ChangeTextStyle(int,int,int); 
void DrawBorder(); 
void MainWindow(char *); 
void Pause(); 
void PutPixelsFromFile(char *,int,int); 
void StatusLine(char *); 
 
void ProgramConstructor(); 
void ProgramDestructor(); 
 
int ErrorCode; 
int GraphDriver; 
int GraphMode; 
int MaxColors; 
int MaxX, MaxY; 
char StringBuffer[80]; 
 
int main() { 
  ProgramConstructor(); 
 
  // Cards are 101 pixels long and 72 pixels wide 
 
  MainWindow( " DECKSHOW, Spades and Hearts (page 1 of 6) " ); 
  PutPixelsFromFile( "AS.PXL",   2,   2 ); 
  PutPixelsFromFile( "2S.PXL", 103,   2 ); 
  PutPixelsFromFile( "3S.PXL", 204,   2 ); 
  PutPixelsFromFile( "4S.PXL", 305,   2 ); 
  PutPixelsFromFile( "5S.PXL",   2,  75 ); 
  PutPixelsFromFile( "6S.PXL", 103,  75 ); 
  PutPixelsFromFile( "7S.PXL", 204,  75 ); 
  PutPixelsFromFile( "8S.PXL", 305,  75 ); 
  PutPixelsFromFile( "9S.PXL",   2, 148 ); 
  PutPixelsFromFile( "TS.PXL", 103, 148 ); 
  PutPixelsFromFile( "JS.PXL", 204, 148 ); 
  PutPixelsFromFile( "QS.PXL", 305, 148 ); 
  PutPixelsFromFile( "KS.PXL",   2, 221 ); 
  PutPixelsFromFile( "AH.PXL",   2, 294 ); 
  PutPixelsFromFile( "2H.PXL", 103, 294 ); 
  PutPixelsFromFile( "3H.PXL", 204, 294 ); 
  PutPixelsFromFile( "4H.PXL", 305, 294 ); 
  PutPixelsFromFile( "5H.PXL",   2, 367 ); 
  PutPixelsFromFile( "6H.PXL", 103, 367 ); 
  PutPixelsFromFile( "7H.PXL", 204, 367 ); 
  PutPixelsFromFile( "8H.PXL", 305, 367 ); 
  PutPixelsFromFile( "9H.PXL",   2, 440 ); 
  PutPixelsFromFile( "TH.PXL", 103, 440 ); 
  PutPixelsFromFile( "JH.PXL", 204, 440 ); 
  PutPixelsFromFile( "QH.PXL", 305, 440 ); 
  PutPixelsFromFile( "KH.PXL",   2, 513 ); 
 
  Pause(); 
 
  MainWindow( " DECKSHOW, Clubs and Diamonds (page 2 of 6) " ); 
  PutPixelsFromFile( "AC.PXL",   2,   2 ); 
  PutPixelsFromFile( "2C.PXL", 103,   2 ); 
  PutPixelsFromFile( "3C.PXL", 204,   2 ); 
  PutPixelsFromFile( "4C.PXL", 305,   2 ); 
  PutPixelsFromFile( "5C.PXL",   2,  75 ); 
  PutPixelsFromFile( "6C.PXL", 103,  75 ); 
  PutPixelsFromFile( "7C.PXL", 204,  75 ); 
  PutPixelsFromFile( "8C.PXL", 305,  75 ); 
  PutPixelsFromFile( "9C.PXL",   2, 148 ); 
  PutPixelsFromFile( "TC.PXL", 103, 148 ); 
  PutPixelsFromFile( "JC.PXL", 204, 148 ); 
  PutPixelsFromFile( "QC.PXL", 305, 148 ); 
  PutPixelsFromFile( "KC.PXL",   2, 221 ); 
  PutPixelsFromFile( "AD.PXL",   2, 294 ); 
  PutPixelsFromFile( "2D.PXL", 103, 294 ); 
  PutPixelsFromFile( "3D.PXL", 204, 294 ); 
  PutPixelsFromFile( "4D.PXL", 305, 294 ); 
  PutPixelsFromFile( "5D.PXL",   2, 367 ); 
  PutPixelsFromFile( "6D.PXL", 103, 367 ); 
  PutPixelsFromFile( "7D.PXL", 204, 367 ); 
  PutPixelsFromFile( "8D.PXL", 305, 367 ); 
  PutPixelsFromFile( "9D.PXL",   2, 440 ); 
  PutPixelsFromFile( "TD.PXL", 103, 440 ); 
  PutPixelsFromFile( "JD.PXL", 204, 440 ); 
  PutPixelsFromFile( "QD.PXL", 305, 440 ); 
  PutPixelsFromFile( "KD.PXL",   2, 513 ); 
 
  Pause(); 
 
  MainWindow( " DECKSHOW, Cardbacks (1) (page 3 of 6) " ); 
  PutPixelsFromFile( "CB0.PXL",   2,   2 ); 
  PutPixelsFromFile( "CB1.PXL", 103,   2 ); 
  PutPixelsFromFile( "CB2.PXL", 204,   2 ); 
  PutPixelsFromFile( "CB3.PXL", 305,   2 ); 
  PutPixelsFromFile( "CB4.PXL",   2,  75 ); 
  PutPixelsFromFile( "CB5.PXL", 103,  75 ); 
  PutPixelsFromFile( "CB6.PXL", 204,  75 ); 
  PutPixelsFromFile( "CB7.PXL", 305,  75 ); 
  PutPixelsFromFile( "CB8.PXL",   2, 148 ); 
  PutPixelsFromFile( "CB9.PXL", 103, 148 ); 
  PutPixelsFromFile( "CBA.PXL", 204, 148 ); 
  PutPixelsFromFile( "CBB.PXL", 305, 148 ); 
  PutPixelsFromFile( "CBC.PXL",   2, 221 ); 
  PutPixelsFromFile( "CBD.PXL", 103, 221 ); 
  PutPixelsFromFile( "CBE.PXL", 204, 221 ); 
  PutPixelsFromFile( "CBF.PXL", 305, 221 ); 
 
  PutPixelsFromFile( "BYC_0.PXL",   2, 294 ); 
  PutPixelsFromFile( "BYC_1.PXL", 103, 294 ); 
  PutPixelsFromFile( "BYC_2.PXL", 204, 294 ); 
  PutPixelsFromFile( "BYC_3.PXL", 305, 294 ); 
  PutPixelsFromFile( "BYC_4.PXL",   2, 367 ); 
  PutPixelsFromFile( "BYC_5.PXL", 103, 367 ); 
  PutPixelsFromFile( "BYC_6.PXL", 204, 367 ); 
  PutPixelsFromFile( "BYC_7.PXL", 305, 367 ); 
  PutPixelsFromFile( "BYC_8.PXL",   2, 440 ); 
  PutPixelsFromFile( "BYC_9.PXL", 103, 440 ); 
  PutPixelsFromFile( "BYC_A.PXL", 204, 440 ); 
  PutPixelsFromFile( "BYC_B.PXL", 305, 440 ); 
  PutPixelsFromFile( "BYC_C.PXL",   2, 513 ); 
  PutPixelsFromFile( "BYC_D.PXL", 103, 513 ); 
  PutPixelsFromFile( "BYC_E.PXL", 204, 513 ); 
  PutPixelsFromFile( "BYC_F.PXL", 305, 513 ); 
 
  Pause(); 
 
  MainWindow( " DECKSHOW, Cardbacks (2) (page 4 of 6) " ); 
  PutPixelsFromFile( "DIAG0.PXL",   2,   2 ); 
  PutPixelsFromFile( "DIAG1.PXL", 103,   2 ); 
  PutPixelsFromFile( "DIAG2.PXL", 204,   2 ); 
  PutPixelsFromFile( "DIAG3.PXL", 305,   2 ); 
  PutPixelsFromFile( "DIAG4.PXL",   2,  75 ); 
  PutPixelsFromFile( "DIAG5.PXL", 103,  75 ); 
  PutPixelsFromFile( "DIAG6.PXL", 204,  75 ); 
  PutPixelsFromFile( "DIAG7.PXL", 305,  75 ); 
  PutPixelsFromFile( "DIAG8.PXL",   2, 148 ); 
  PutPixelsFromFile( "DIAG9.PXL", 103, 148 ); 
  PutPixelsFromFile( "DIAGA.PXL", 204, 148 ); 
  PutPixelsFromFile( "DIAGB.PXL", 305, 148 ); 
  PutPixelsFromFile( "DIAGC.PXL",   2, 221 ); 
  PutPixelsFromFile( "DIAGD.PXL", 103, 221 ); 
  PutPixelsFromFile( "DIAGE.PXL", 204, 221 ); 
  PutPixelsFromFile( "DIAGF.PXL", 305, 221 ); 
 
  Pause(); 
 
  MainWindow( " DECKSHOW, misc (page 5 of 6) " ); 
 
  PutPixelsFromFile( "CARDHOLE.PXL",   2,   2 ); 
  PutPixelsFromFile( "Z2.PXL",       103,   2 ); 
  PutPixelsFromFile( "BLACKOUT.PXL", 204,   2 ); 
  PutPixelsFromFile( "ROYAL.PXL",    305,   2 ); 
 
  PutPixelsFromFile( "Z1.PXL",         2,  75 ); 
  PutPixelsFromFile( "DECKSIDE.PXL", 103,  75 ); 
 
  PutPixelsFromFile( "NORTHWRD.PXL",   2, 294 ); 
  PutPixelsFromFile( "SOUTHWRD.PXL",  32, 294 ); 
  PutPixelsFromFile( "EASTWORD.PXL",  62, 294 ); 
  PutPixelsFromFile( "WESTWORD.PXL",  92, 294 ); 
  PutPixelsFromFile( "SUIT.PXL",     122, 294 ); 
  PutPixelsFromFile( "WHONE.PXL",    152, 294 ); 
  PutPixelsFromFile( "WHTWO.PXL",    152, 324 ); 
  PutPixelsFromFile( "WHTHREE.PXL",  152, 354 ); 
  PutPixelsFromFile( "WHFOUR.PXL",   152, 384 ); 
  PutPixelsFromFile( "WHFIVE.PXL",   152, 414 ); 
  PutPixelsFromFile( "WHSIX.PXL",    152, 444 ); 
  PutPixelsFromFile( "BRONE.PXL",    182, 294 ); 
  PutPixelsFromFile( "BRTWO.PXL",    182, 324 ); 
  PutPixelsFromFile( "BRTHREE.PXL",  182, 354 ); 
  PutPixelsFromFile( "BRFOUR.PXL",   182, 384 ); 
  PutPixelsFromFile( "BRFIVE.PXL",   182, 414 ); 
  PutPixelsFromFile( "BRSIX.PXL",    182, 444 ); 
  PutPixelsFromFile( "WH_2.PXL",     212, 294 ); 
  PutPixelsFromFile( "WH_4.PXL",     212, 324 ); 
  PutPixelsFromFile( "WH_8.PXL",     212, 354 ); 
  PutPixelsFromFile( "WH16.PXL",     212, 384 ); 
  PutPixelsFromFile( "WH32.PXL",     212, 414 ); 
  PutPixelsFromFile( "WH64.PXL",     212, 444 ); 
 
  Pause(); 
 
  MainWindow( " DECKSHOW, Magjong (page 6 of 6) " ); 
  PutPixelsFromFile( "DOT1.PXL",   2,   2 ); 
  PutPixelsFromFile( "DOT2.PXL",   2,  35 ); 
 
  Pause(); 
 
  ProgramDestructor(); 
 
  return 0; 
} 
 
void MainWindow(char *Header) { 
  int Height; 
 
  cleardevice(); 
  setcolor( MaxColors - 1 ); 
  setviewport( 0, 0, MaxX, MaxY, 1 ); 
 
  Height = textheight( "H" ); 
 
  ChangeTextStyle( DEFAULT_FONT, HORIZ_DIR, 1 ); 
  settextjustify( CENTER_TEXT, TOP_TEXT ); 
  outtextxy( MaxX/2, 2, Header ); 
  setviewport( 0, Height+4, MaxX, MaxY-(Height+4), 1 ); 
  DrawBorder(); 
  setviewport( 1, Height+5, MaxX-1, MaxY-(Height+5), 1 ); 
} 
 
void ChangeTextStyle(int Font, int Direction, int CharSize) { 
  int ErrorCode; 
 
  graphresult(); 
  settextstyle(Font, Direction, CharSize); 
  ErrorCode = graphresult(); 
  if( ErrorCode != grOk ){ 
    closegraph(); 
    textmode( C4350 ); 
    clrscr(); 
    printf( "Graphics System Error in Module ChangeTextStyle:\n\n%s\n", 
      grapherrormsg( ErrorCode ) ); 
    exit( 3 ); 
  } 
} 
 
void StatusLine(char *Message) { 
  int Height; 
 
  setviewport( 0, 0, MaxX, MaxY, 1 ); 
  setcolor( MaxColors - 1 ); 
 
  ChangeTextStyle( DEFAULT_FONT, HORIZ_DIR, 1 ); 
  settextjustify( CENTER_TEXT, TOP_TEXT ); 
  setlinestyle( SOLID_LINE, 0, NORM_WIDTH ); 
  setfillstyle( EMPTY_FILL, 0 ); 
 
  Height = textheight( "H" ); 
  bar( 0, MaxY-(Height+4), MaxX, MaxY ); 
  rectangle( 0, MaxY-(Height+4), MaxX, MaxY ); 
  outtextxy( MaxX/2, MaxY-(Height+2), Message ); 
  setviewport( 1, Height+5, MaxX-1, MaxY-(Height+5), 1 ); 
} 
 
void DrawBorder() { 
  struct viewporttype ViewPort; 
 
  setcolor( MaxColors - 1 ); 
 
  setlinestyle( SOLID_LINE, 0, NORM_WIDTH ); 
 
  getviewsettings( &ViewPort ); 
  rectangle( 0, 0, ViewPort.right-ViewPort.left, 
    ViewPort.bottom-ViewPort.top ); 
} 
 
void PutPixelsFromFile(char *filename, int Yref, int Xref) { 
  int x, y=0, Color; 
  FILE *in; 
  int Width; 
  char sb[640]; 
 
  sprintf(StringBuffer,"%s%s",PATH_TO_CARDS,filename); 
  if ( (in = fopen(StringBuffer, "rb")) != NULL ) { 
 
  fgets(sb, 640, in ); 
  while ( !feof(in) ) { 
    Width = strlen(sb); 
    for (x=0; x<Width; x++) { 
      Color = -1; 
      switch (sb[x]) { 
      case '0': Color =  0; break; 
      case '1': Color =  1; break; 
      case '2': Color =  2; break; 
      case '3': Color =  3; break; 
      case '4': Color =  4; break; 
      case '5': Color =  5; break; 
      case '6': Color =  6; break; 
      case '7': Color =  7; break; 
      case '8': Color =  8; break; 
      case '9': Color =  9; break; 
      case 'A': Color = 10; break; 
      case 'B': Color = 11; break; 
      case 'C': Color = 12; break; 
      case 'D': Color = 13; break; 
      case 'E': Color = 14; break; 
      case 'F': Color = 15; break; 
      } 
      if (Color != -1) putpixel( x+Xref, y+Yref, Color ); 
    } 
    y++; 
    fgets(sb, 640, in ); 
  } 
  fclose( in ); 
 
  } 
} 
 
void Pause() { 
  static char Message[] = "PAUSED for VIEWING. Press a key..."; 
  int c; 
 
  StatusLine( Message ); 
  c = getch(); 
  if ( c == ESC ) { 
    closegraph(); 
    textmode( C4350 ); 
    clrscr(); 
    exit( 5 ); 
  } 
  if ( 0 == c ) c = getch(); 
  cleardevice(); 
} 
 
void ProgramConstructor() { 
  GraphDriver = DETECT; 
  initgraph( &GraphDriver, &GraphMode, PATH_TO_BGI ); 
  ErrorCode = graphresult(); 
  if ( ErrorCode != grOk ) { 
    closegraph(); 
    textmode( C4350 ); 
    clrscr(); 
    printf( "Graphics Error:\n\n%s\n", grapherrormsg( ErrorCode )); 
    exit( 2 ); 
  } 
  StringBuffer[0] = 0x00; 
  MaxColors = getmaxcolor() + 1; 
  MaxX = getmaxx(); 
  MaxY = getmaxy(); 
} 
 
void ProgramDestructor() { 
  closegraph(); 
  textmode( C4350 ); 
  clrscr(); 
}
```

---

### Post by randallecook on 2011-04-29
While this thread probably belongs in one of the developer forums, I'll try to answer it here.

You certainly could drive Qt directly from your old files, but it might be easier to transform them into a newer format first. For example, the netpbm format is very easy to work with: [http://en.wikipedia.org/wiki/Netpbm_format](http://en.wikipedia.org/wiki/Netpbm_format). Once in this format, most graphics apps can read the files, or you could use a tool like imagemagick to transform them into something else, like JPEG or PNG.

If you really want to display the legacy images onscreen in a program you control, then you'll have to learn Qt or JUCE or some other UI framework, and that's a little bigger topic than I can answer here. Best of luck to you, and for bringing old graphics formats back to life!

p.s. In any event you'll have to create a mapping from the 16 color codes in the original files to RGB values. That should be the fun part.

---

### Post by machdohvah on 2011-04-30
> **randallecook said:**
> While this thread probably belongs in one of the developer forums, I'll try to answer it here.

You certainly could drive Qt directly from your old files, but it might be easier to transform them into a newer format first. For example, the netpbm format is very easy to work with: [http://en.wikipedia.org/wiki/Netpbm_format](http://en.wikipedia.org/wiki/Netpbm_format). Once in this format, most graphics apps can read the files, or you could use a tool like imagemagick to transform them into something else, like JPEG or PNG.

If you really want to display the legacy images onscreen in a program you control, then you'll have to learn Qt or JUCE or some other UI framework, and that's a little bigger topic than I can answer here. Best of luck to you, and for bringing old graphics formats back to life!

p.s. In any event you'll have to create a mapping from the 16 color codes in the original files to RGB values. That should be the fun part.

I cannot thank you enough. On that web site I found a format known as PPM. I created a program, see below, that successfully converted my old clunky DOS generated PXL format as described above into a binary PPM format (P6). After loading the result in the image viewer I was able to create my first JPEG version of my two of spades (2s.jpeg).I have never got that far before. THANK YOU!

```
#define PROGNAM "PXL2PPM6" 
#define AUTHOR "Michael Flower" 
#define VERSION "30Apr2011" 
 
/* 
 
30Apr2011 Creating this program from scratch to translate the PXL format 
that I created long ago to a standard known as PPM. 
 
PXL format is one byte per color ranging from 0 to 15 representing the 
16 colors of the old DOS screen. Each line ends with a \x0D0A. 
 
PPM format starts with "P6" followed by \x0a. Then the number of rows 
and the number of columns in ASCII and newline. A line may exist that 
starts with a "#". These are comment lines and are to be ignored. The 
next line has "255" declaring that the color depth is 256 colors. Then 
each line that follow are RGB triplets in binary. 
 
*/ 
 
#include <stdio.h> 
#include <stdlib.h> 
#include <string.h> 
 
void translate_this_byte(); 
 
char filename[12]; 
char s[80]; 
int numcols = 0; 
int numrows = 0; 
FILE *infile; 
FILE *outfile; 
 
int main(int argc, char* argv[]) { 
  int i, j; 
 
  if ( argc >= 2 ) { 
    strcpy( filename, argv[1] ); 
    numcols = atoi( argv[2] ); 
    numrows = atoi( argv[3] ); 
  } else { 
    printf("%s filename numcols numrows\n\n", PROGNAM); 
    printf("%s needs a file name without extension in the first argument.\n\n", PROGNAM); 
    printf("Author: %s\n", AUTHOR); 
    printf("Version: %s\n\n", VERSION); 
    exit(1); 
  } 
  if (numcols <= 0) { 
    printf("%s filename numcols numrows\n\n", PROGNAM); 
    printf("%s needs the number of columns in the second argument.\n\n", PROGNAM); 
    printf("Author: %s\n", AUTHOR); 
    printf("Version: %s\n\n", VERSION); 
    exit(1); 
  } 
  if (numrows <= 0) { 
    printf("%s filename numcols numrows\n\n", PROGNAM); 
    printf("%s needs the number of rows in the third argument.\n\n", PROGNAM); 
    printf("Author: %s\n", AUTHOR); 
    printf("Version: %s\n\n", VERSION); 
    exit(1); 
  } 
  strcpy( s, "PXL/" ); 
  strcat( s, filename ); 
  strcat( s, ".PXL" ); 
  if (( infile = fopen( s, "rt" )) == NULL ) { 
    printf( "Cannot open input file: %s.\n\n", s ); 
    exit(2); 
  } 
  strcpy( s, "PPM6/" ); 
  strcat( s, filename ); 
  strcat( s, ".PPM" ); 
  if (( outfile = fopen( s, "wb" )) == NULL ) { 
    printf( "Unable to create binary output file: %s.\n\n", s ); 
    fclose(infile); 
    exit(3); 
  } 
 
  fprintf( outfile, "P6" ); 
  fputc( '\x0a', outfile ); 
  fprintf( outfile, "# %s.PXL file translated here in PPM binary format", filename ); 
  fputc( '\x0a', outfile ); 
  fprintf( outfile, "%s %s", argv[2], argv[3]); 
  fputc( '\x0a', outfile ); 
  fprintf( outfile, "255"); 
  fputc( '\x0a', outfile ); 
 
  for(i=0;i<numrows;i++) { 
    for(j=0;j<(numcols+2);j++) { 
      translate_this_byte(); 
    } 
  } 
 
  return 0 ; 
} 
 
void translate_this_byte() { 
  int this_byte; 
 
  this_byte = fgetc( infile ); 
  switch (this_byte) { 
  case '\x0a': 
  case '\x0d': 
    break; 
  case '0': // Black 
    fputc( '\x00', outfile ); 
    fputc( '\x00', outfile ); 
    fputc( '\x00', outfile ); 
    break; 
  case '1': // Blue 
    fputc( '\x00', outfile ); 
    fputc( '\x00', outfile ); 
    fputc( '\x80', outfile ); 
    break; 
  case '2': // Green 
    fputc( '\x00', outfile ); 
    fputc( '\x80', outfile ); 
    fputc( '\x00', outfile ); 
    break; 
  case '3': // Cyan 
    fputc( '\x00', outfile ); 
    fputc( '\x80', outfile ); 
    fputc( '\x80', outfile ); 
    break; 
  case '4': // Red 
    fputc( '\x80', outfile ); 
    fputc( '\x00', outfile ); 
    fputc( '\x00', outfile ); 
    break; 
  case '5': // Magenta 
    fputc( '\x80', outfile ); 
    fputc( '\x00', outfile ); 
    fputc( '\x80', outfile ); 
    break; 
  case '6': // Brown 
    fputc( '\x80', outfile ); 
    fputc( '\x80', outfile ); 
    fputc( '\x00', outfile ); 
    break; 
  case '7': // Light Grey 
    fputc( '\x80', outfile ); 
    fputc( '\x80', outfile ); 
    fputc( '\x80', outfile ); 
    break; 
  case '8': // Dark Grey 
    fputc( '\x3f', outfile ); 
    fputc( '\x3f', outfile ); 
    fputc( '\x3f', outfile ); 
    break; 
  case '9': // Bright Blue 
    fputc( '\x00', outfile ); 
    fputc( '\x00', outfile ); 
    fputc( '\xff', outfile ); 
    break; 
  case 'A': // Bright Green 
    fputc( '\x00', outfile ); 
    fputc( '\xff', outfile ); 
    fputc( '\x00', outfile ); 
    break; 
  case 'B': // Bright Cyan 
    fputc( '\x00', outfile ); 
    fputc( '\xff', outfile ); 
    fputc( '\xff', outfile ); 
    break; 
  case 'C': // Bright Red 
    fputc( '\xff', outfile ); 
    fputc( '\x00', outfile ); 
    fputc( '\x00', outfile ); 
    break; 
  case 'D': // Bright Magenta 
    fputc( '\xff', outfile ); 
    fputc( '\x00', outfile ); 
    fputc( '\xff', outfile ); 
    break; 
  case 'E': // Yellow 
    fputc( '\xff', outfile ); 
    fputc( '\xff', outfile ); 
    fputc( '\x00', outfile ); 
    break; 
  default: // White (or anything else) 
    fputc( '\xff', outfile ); 
    fputc( '\xff', outfile ); 
    fputc( '\xff', outfile ); 
    break; 
  } 
}
```

---

