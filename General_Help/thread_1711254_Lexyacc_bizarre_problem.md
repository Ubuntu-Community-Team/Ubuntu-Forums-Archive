---
title: "Lex/yacc bizarre problem"
date: 2011-03-21
forum: General Help
---

### Post by Ibn_Al_Arabi on 2011-03-21
Hello all ,

I'm writing a parser using lex and yacc for an IEEE standard language ( STIL ). Here's the lex file ( some of ).

/* C inclusion C and other GV */
%%
/*
Other RE
*/
dig     [0-9]
num1         {dig}+\.?([eE][-+]?{dig}+)?
num2         {dig}*\.{dig}+([eE][-+]?{dig}+)?
number       {num1}|{num2}
/*
Other RE
*/
%%
/*
Some rules
*/
{number}        {if(!bus) {return(NUM);} if (bus) REJECT;}
/*
Other rules
*/

 The yac file is this way :

stil_language :
    STIL_statement top_level_statements
    {
        bus = 0;
    }
    ;

STIL_statement :
    STIL NUM ';'
    | STIL NUM {any=1;} '{' anything_statements_plus '}' {any=0;}
    ;

stil_language is the start  symbol.

The bus variable is initialised at 0 ( There's a check in the main ).

The problem is that the parser does not recognises the NUM token ! It just re writes any expression that corresponds to the "number" regular expression.

Here's a prompt example :

[B]user@pc_of_user{stil_directory} : parser
bus =0 , any = 0
*STIL 1.0 ;*
 1.0 _bus =0 , any = 0 ; Syntax error : --> unexpected ';'_
[/B]

What's underlined is yyerror. I wrote what's italic

Do someone , please , have an idea about what the error might be ?

---

### Post by Ibn_Al_Arabi on 2011-03-21
Look at this , I tryed to find out the problem which seems to be with the . character :

**lex file :**

[I]%option noyywrap

ws    [ \t]+
dig     [0-9]
simple_float {dig}+.{dig}+
num1         {dig}+\.?([eE][-+]?{dig}+)?
num2         {dig}*\.{dig}+([eE][-+]?{dig}+)?
number       {num1}|{num2}

%%

\n            {mylineno++; if( any && g_flagKeyWord ) fprintf(g_fUserKFile,"%s",yytext);}
{number}        {printf("OK5\n"); if(!bus) {return(NUM);} if (bus) REJECT;}
STIL        {return(STIL);}
"//".*          {if(g_flagKeyWord) REJECT; while(input()!='\n') ; mylineno++;}
"/*"        {
            register int c;
            for ( ; ; )
                {
                               while ( (c = input()) != '*' &&
                                       c != EOF && c != '\n')
                                  ;    // eat up text of comment

                        if ( c == '*' )
                                  {
                                  while ( (c = input()) == '*' )
                                      ;
                                  if ( c == '/' )
                                      break;    /* found the end */
                                  }

                              if ( c == EOF )
                                  {
                                  printf( "EOF in comment ERROR" );
                                  break;
                                  }

                              if (c == '\n')
                  {
                  mylineno++;
                  /* break; */
                  }
                              }
                          }
Ann[ \t]*"{*"        {
        loop2:
                
                  while(input()!='*');
                  switch(input()){
          case '\n' :
            mylineno++;
            goto loop2;
                  case '}':
            /* return(ANNCOMMENT); */
                    break;
                  case '*':
                    unput('*');
          default:
            goto loop2;
          }
                }
"\\"    {printf("syntax error !");}
%%[/I]

**yac file :**

%start stil_language
%token NUM STIL
%left  '+' '-'
%left  '*' '/' /* left associative, higher precedence */
%left  UNARYMINUS

%%

stil_language :
    STIL_statement
    {
        printf("OK1\n");
        bus = 0;
    }
    ;

STIL_statement :
    STIL {printf("OK2\n");} NUM {printf("OK3\n");} ';' {printf("OK4\n");}
    ;                    
                        
                        
%%

extern char *yytext;
extern char * yytname;

int yyerror(char *s)
{
        //char* msg;
        //if (!StilNotSupportFeature) {
        //msg = (char *) malloc(strlen(s)+strlen(yytext)+200);
    printf ("bus = %d , any = %d\n" , bus , any );
        printf("Syntax error : --> unexpected '%s'\n" ,yytext);

#ifdef DEBUG
if (yychar!=YYEMPTY) {
printf("\n** line %d ** : %s --> %s (%s)\n", mylineno, s, yytext, yytname[YYTRANSLATE(yychar)]);
}
#endif
}
int main (int argc , char * argv[])
{
    printf ("bus = %d , any = %d " , bus , any );    
    if ( argc == 2 )
    yyin = fopen ( argv[1] , "r" );
    else if ( argc >= 3 )
    {
    yyout = fopen ( argv[2] , "w" );
    yyin =     fopen ( argv[1] , "r" );
    }
    yyparse();
    if ( argc == 2 )
    fclose ( yyin ) ;
    if ( argc >= 3) 
    fclose ( yyout ) ;
    return 1 ;
}

**The execution of this parser gives :**

user@user_s_place{user_dir} : ./exec stil_6.yac stil_6.lex
bus = 0 , any = 0 *STIL 1.0 ;*
OK2
 1.0 ;

I wrote what's in italic ... Any help ?

---

