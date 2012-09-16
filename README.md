code
====import java.awt.*;
import java.awt.event.*;
import java.applet.*;
import javax.swing.*;
import java.io.*;
import java.io.FilePermission;
import java.lang.*;
import java.security.AllPermission;


/*
<applet code="af2.class" width=1366 height=600>
</applet>
*/

// Create a subclass of Frame
class MenuFrame extends JFrame implements ActionListener {
String msg = " ",str;
Font fn;
String sr,s;
 JLabel l1,l2,l3,l4,l5,l6,l7,l8;
JTextField text2,text3;
 TextArea text1,text;
JButton b1,b2,b3,b4,b5,b6,b7;
JPanel f;
FileDialog fd=new FileDialog(this,"File Dialog",FileDialog.LOAD);

char[][] a=new char[2][1000000];


//md5 variables

File f1,f2;
 String st,mdvv;  
  long  n,m,len;
 int i,k,mo;
 int c;
//String buf[],aa,bb,cc,dd;
int aa,bb,cc,dd,e,fa,g,h,ee,ff,gg,hh;
//buf = new String[4];
//int buf[],t[];
//FileReader fr;
//FileWriter fw;
int buf[]= new int[4];
int sh[]=new int[65];
int t[]=new int[65];
 
//mdd md;





MenuFrame(String title) {
super(title);
// create menu bar and add it to frame
MenuBar mbar = new MenuBar();
setMenuBar(mbar);
// create the menu items
Menu file = new Menu("File");
MenuItem item1, item2, item3, item4;
file.add(item1 = new MenuItem("Open"));
file.add(item2 = new MenuItem("Exit"));
mbar.add(file);
Menu edit = new Menu("About");
edit.add(item3 = new MenuItem("Software"));
edit.add(item4 = new MenuItem("Developer"));
mbar.add(edit);


setLayout(null);
//f.setSize(1366,600);
//f.setVisible(true);
fn = new Font("Dialog", Font.PLAIN, 20);
l1=new JLabel("INPUT ");
l2=new JLabel("PROCESS");
l3=new JLabel("OUTPUT");

text1=new TextArea( 20, 30);
b3=new JButton("CANCEL");
b1=new JButton("ESTART");
b2=new JButton("DECRYPT");
b4=new JButton("ENCRYPT");
b5=new JButton("DSTART");

text = new TextArea( 30, 30);

l6=new JLabel("DATA INTEGRITY");
l5=new JLabel(" DATA CONFIDENTIALITY");
l4=new JLabel(" VIRUS CHECK");
f=new JPanel();

this.add(text);
this.add(l1);
this.add(l2);
this.add(b3);
this.add(b1);
this.add(b2);
this.add(b4);
this.add(b5);
this.add(l3);
this.add(text1);
l6=new JLabel("DATA INTEGRITY");
l5=new JLabel(" DATA CONFIDENTIALITY");
l4=new JLabel(" VIRUS CHECK");
this.add(l4);
this.add(l5);
this.add(l6);
text2=new JTextField();
text2.setColumns(8);
text3=new JTextField();
l7 =new JLabel("ENTER KEY:");
l8=new JLabel("ENTER ROUNDS:");
b6=new JButton("SUBMIT");
b7=new JButton("SUBMIT1");
this.add(text2);
this.add(text3);
this.add(l7);
this.add(l8);
this.add(b6);
this.add(b7);

l1.setBounds(140,20,200,30);
l2.setBounds(1079,20,200,30);
text1.setBounds(20,60,450,300);
b3.setBounds(170,500,100,30);
b1.setBounds(110,400,100,30);
b4.setBounds(110,450,100,30);
b2.setBounds(240,400,100,30);
b5.setBounds(240,450,100,30);
text.setBounds(500,60,450,300);
l3.setBounds(630,20,200,30);
b3.addActionListener(this);
b1.addActionListener(this);
b2.addActionListener(this);
b4.addActionListener(this);
b5.addActionListener(this);
b6.addActionListener(this);
text2.addActionListener(this);
text3.addActionListener(this);
b7.addActionListener(this);
l2.setFont(fn);
l1.setFont(fn);
l3.setFont(fn);


// register it to receive those even
item1.addActionListener(this);
item2.addActionListener(this);
item3.addActionListener(this);
item4.addActionListener(this);

// create an object to handle window events
//MyWindowAdapter adapter = new MyWindowAdapter(this);
// register it to receive those events
//addWindowListener(adapter);





sh[1]=7 ;  sh[2]=12 ; sh[3]=17 ; sh[4]=22 ;  sh[5]=7 ;  sh[6]=12 ;  sh[7]=17 ;  sh[8]=22 ;
sh[9]=7 ;  sh[10]= 12; sh[11]=17 ; sh[12]=22 ;  sh[13]=7 ;  sh[14]=12 ;  sh[15]=17 ;  sh[16]=22 ;
sh[17]= 5;  sh[18]= 9; sh[19]= 14; sh[20]=20 ;  sh[21]=5 ;  sh[22]=9 ;  sh[23]=14 ;  sh[24]=20 ;
sh[25]=5 ;  sh[26]= 9; sh[27]= 14; sh[28]=20 ;  sh[29]= 5;  sh[30]=9 ;  sh[31]=14 ;  sh[32]=20 ;
sh[33]=4 ;  sh[34]=11 ; sh[35]=16 ; sh[36]=23 ;  sh[37]=4 ;  sh[38]=11 ;  sh[39]=16 ;  sh[40]=23 ;
sh[41]=4 ;  sh[42]=11 ; sh[43]=16 ; sh[44]=23 ;  sh[45]=4 ;  sh[46]=11 ;  sh[47]=16 ;  sh[48]=23 ;
sh[49]= 6;  sh[50]=10 ; sh[51]=15 ; sh[52]=21 ;  sh[53]=6 ;  sh[54]=10 ;  sh[55]=15 ;  sh[56]=21 ;
sh[57]=6 ;  sh[58]=10 ; sh[59]=15 ; sh[60]= 21;  sh[61]=6 ;  sh[62]=10 ;  sh[63]=15 ;  sh[64]=21 ; 
 


                buf[0] = 0x67452301;
  	buf[1] = 0xefcdab89;
		buf[2] = 0x98badcfe;
		buf[3] = 0x10325476;

t[1]=0xd76aa478; t[2]=0xe8c7b756; t[3]=0x242070db; t[4]=0xc1bdceee; t[5]=0xf57c0faf; t[6]=0x4787c62a; t[7]=0xa8304613; t[8]=0xfd469501; 
t[9]=0x698098d8; t[10]=0x8b44f7af; t[11]=0xffff5bb1;t[12]=0x895cd7be; t[13]=0x6b901122; t[14]=0xfd987193; t[15]=0xa679438e; t[16]=0x49b40821; 
t[17]=0xf61e2562; t[18]=0xc040b340; t[19]=0x265e5a51; t[20]=0xe9b6c7aa; t[21]=0xd62f105d; t[22]=0x02441453; t[23]=0xd8a1e681; t[24]=0xe7d3fbc8; 
t[25]=0x21e1cde6; t[26]=0xc33707d6; t[27]=0xf4d50d87; t[28]=0x455a14ed; t[29]=0xa9e3e905; t[30]=0xfcefa3f8; t[31]=0x676f02d9; t[32]=0x8d2a4c8a; 
t[33]=0xfffa3942; t[34]=0x8771f681; t[35]=0x699d6122; t[36]=0xfde5380c; t[37]=0xa4beea44; t[38]=0x4bdecfa9; t[39]=0xf6bb4b60; t[40]=0xbebfbc70; 
t[41]=0x289b7ec6; t[42]=0xeaa127fa; t[43]=0xd4ef3085; t[44]=0x04881d05; t[45]=0xd9d4d039; t[46]=0xe6db99e5; t[47]=0x1fa27c78; t[48]=0xc4ac5665; 
t[49]=0xf4292244; t[50]=0x432aff97; t[51]=0xab9423a7; t[52]=0xfc93a039; t[53]=0x655b59c3; t[54]=0x8f0ccc92; t[55]=0xffeff47d; t[56]=0x85845dd1; 
t[57]=0x6fa87e4f; t[58]=0xfe2ce6e0; t[59]=0xa3014314; t[60]=0x4e0811a1; t[61]=0xf7537e82; t[62]=0xbd3af235; t[63]=0x2ad7d2bb; t[64]=0xeb86d391;


}



public void actionPerformed(ActionEvent ae)
 {
s=ae.getActionCommand();
if(s=="Open")
{

try{
fd.setVisible(true);
str=fd.getDirectory();
str+=fd.getFile();
//text.setText(str);

File f2=new File(str);
//double val=Math.pow(2,32);
//System.out.println(val);
FileReader fr=new FileReader(f2);
int le=(int)(f2.length());
fr.read(a[1],0,le);
sr=new String(a[1]);
//sr="open";
text1.setText(sr);
}
catch(Exception e){
text.setText(e.toString());
}

}
else if(s=="ESTART")
{
l4.setBounds(1055,130,200,30);
l4.setEnabled(true);
l6.setBounds(1055,180,200,30);
l5.setBounds(1055,230,200,30);
l5.setEnabled(true);
l6.setEnabled(true);

vir2 v2=new vir2();
int vv=v2.virus(str);


if(vv == 1)
{
text.setText("Virus found and necessary actions taken");
JOptionPane.showMessageDialog(null, "VIRUS FOUND AND NECESSARY ACTIONS TAKEN", "CIA", 1);
}
else
{
text.setText("No virus found");
JOptionPane.showMessageDialog(null, "NO VIRUS FOUND", "CIA", 1);
}


 try
{

Thread.sleep(3000);
 f1=new File(str);
 f2=new File("D:/wtext.txt");
 FileReader fr=new FileReader(f1);
 FileWriter fw=new FileWriter(f2);
 BufferedReader br = new BufferedReader(fr);
 len=f1.length();
 System.out.println("Length of the given file is"+len);


while((c = fr.read()) != -1)
{
if(c<58 && c>47)
{
 c=c-48;
}
s=Integer.toBinaryString(c);
c=s.length();
switch(c)
{
case 0:
fw.write("00000000");
break;
case 1:
fw.write("0000000");
fw.write(s);
break;
case 2:
fw.write("000000");
fw.write(s);
break;
case 3:
fw.write("00000");
fw.write(s);
break;
case 4:
fw.write("0000");
fw.write(s);
break;
case 5:
fw.write("000");
fw.write(s);
break;
case 6:
fw.write("00");
fw.write(s);
break;
case 7:
fw.write("0");
fw.write(s);
break;
case 8:
fw.write(s);
break;
}
}
//fr.close();
//fw.close();

n=f2.length();
System.out.println(n);

s=null;
//APPEND PADDING BITS AND LENGTH:
if((len*8) < 448)
{
 m=448-(len*8);
 fw.write("1");
 for(i=0;i<m-1;i++)
 { 
   fw.write("0");
 }
System.out.println("Length of the test1 file is"+f2.length());
System.out.println("Binary equivalent of the "+len+" is " +Integer.toBinaryString((int)len));
s=Integer.toBinaryString((int)len);
m=s.length();
System.out.println("Length of the length"+m);
m=64-m;
 for(i=0;i<m;i++)
 { 
   fw.write("0");
 }
fw.write(s);
fr.close();
fw.close();
System.out.println("Length of the test1 file is"+f2.length());
}
else
{
m=(len*8)%512;
if(m<448)
{

 m=448-m;
 fw.write("1");
 for(i=0;i<m-1;i++)
 { 
   fw.write("0");
 }
System.out.println("Length of the test1 file is"+f2.length());
System.out.println("Binary equivalent of the "+len+" is " +Integer.toBinaryString((int)len));
s=Integer.toBinaryString((int)len);
m=s.length();
System.out.println("Length of the length"+m);
m=64-m;
 for(i=0;i<m;i++)
 { 
   fw.write("0");
 }
fw.write(s);
fr.close();
fw.close();
System.out.println("Length of the test1 file is"+f2.length());
}
else if(m>=448)
{

m=512-m;
fw.write("1");
for(i=0;i<m+447;i++)
{
fw.write("0");
}
System.out.println("Binary equivalent of the "+len+" is " +Integer.toBinaryString((int)len));
s=Integer.toBinaryString((int)len);
m=s.length();
System.out.println("Length of the length"+m);
m=64-m;
 for(i=0;i<m;i++)
 { 
   fw.write("0");
 }
fw.write(s);
fr.close();
fw.close();
System.out.println("Length of the test1 file is"+f2.length());
}
}
//processing of 512 block

aa=buf[0];
bb=buf[1];
cc=buf[2];
dd=buf[3];


double val=Math.pow(2,32);
//System.out.println(val);
fr=new FileReader(f2);

char[][] ar=new char[2][1000000];
int le=(int)(f2.length());
fr.read(ar[1],0,le);
String str=new String(ar[1]);
//System.out.println(st);
len=f2.length();
System.out.println(len);
len=len/512;
System.out.println(len);

k=1;
mo=0;
int flag;
flag=0;
for(int count=0;count<len;count++)
{

ee=aa;
ff=bb;
gg=cc;
hh=dd;

int flen=count*512;
int flen1=flen+512;
st=str.substring(flen,flen1);
k=1;
mo=0;
//flag=flag+1;
//System.out.println("before round "+ flag);
//Round 1:

for(i=1;i<17;i++)
{
aa = (int)( (aa+ ((bb & cc) | (~bb & dd)) ) % val);
aa=(int)((aa+t[i])%val);
int mod=mo*32;
int ko=k*32;
mo++;
k++;
s=st.substring(mod,ko);
if((long)Long.parseLong(s,2) >  2147483647)
{
  long lon=(long)Long.parseLong(s,2)% 2147483647L;
  s=Long.toBinaryString(lon);
  int valu=s.length();
int jnn=32-valu;
for(int k1=0;k1<jnn;k1++)
{
 s='0'+s;
}
  s=s.substring(s.length()-32,s.length());
}

int go=Integer.parseInt(s,2);
aa=(int)((aa+go)%val);
aa = (aa << sh[i]) | (aa >>> (32 - sh[i]));
aa=(int)((aa+bb)%val);
e=aa;
fa=bb;
g=cc;
h=dd;
bb=e;cc=fa;dd=g;aa=h;
}

//flag=flag+1;

//System.out.println("before round " + flag);

//Round 2:

int j=0;
for(i=17;i<33;i++)
{
aa =(int)((aa+ ((bb & dd) | (cc & ~dd)))%val);
aa=(int)((aa+t[i])%val);
int mod=((1+(5*j))%16)*32;
int ko=mod+32;
j++;
s=st.substring(mod,ko);
if((long)Long.parseLong(s,2) >  2147483647)
{
  long lon=(long)Long.parseLong(s,2)% 2147483647L;
  s=Long.toBinaryString(lon);
  int valu=s.length();
int jnn=32-valu;
for(int k1=0;k1<jnn;k1++)
{
 s='0'+s;
}
  s=s.substring(s.length()-32,s.length());
}

int go=Integer.parseInt(s,2);
aa=(int)((aa+go)%val);
aa = (aa << sh[i]) | (aa >>> (32 - sh[i]));
aa=(int)((aa+bb)%val);
e=aa;
fa=bb;
g=cc;
h=dd;
bb=e;cc=fa;dd=g;aa=h;
}

//flag=flag+1;

//System.out.println("before round "+flag);

//Round 3:

 j=0;
for(i=33;i<49;i++)
{
aa = (int)((bb ^ cc ^ dd)%val);
aa=(int)((aa+t[i])%val);
int mod=((5+(3*j))%16)*32;
int ko=mod+32;
j++;
s=st.substring(mod,ko);
if((long)Long.parseLong(s,2) >  2147483647)
{
  long lon=(long)Long.parseLong(s,2)% 2147483647L;
  s=Long.toBinaryString(lon);
  int valu=s.length();
int jnn=32-valu;
for(int k1=0;k1<jnn;k1++)
{
 s='0'+s;
}
  s=s.substring(s.length()-32,s.length());
}

int go=Integer.parseInt(s,2);
aa=(int)((aa+go)%val);
aa = (aa << sh[i]) | (aa >>> (32 - sh[i]));
aa=(int)((aa+bb)%val);
e=aa;
fa=bb;
g=cc;
h=dd;
bb=e;cc=fa;dd=g;aa=h;
}



//flag=flag+1;
//System.out.println("before round "+flag);

//Round 4:

j=0;
for(i=49;i<=64;i++)
{
aa =(int)((aa+ (cc ^ (bb | ~dd)))%val);
aa=(int)((aa+t[i])%val);
int mod=((7*j)%16)*32;
int ko=mod+32;
j++;
s=st.substring(mod,ko);
if((long)Long.parseLong(s,2) >  2147483647)
{
  long lon=(long)Long.parseLong(s,2)% 2147483647L;
  s=Long.toBinaryString(lon);
  int valu=s.length();
int jnn=32-valu;
for(int k1=0;k1<jnn;k1++)
{
 s='0'+s;
}
  s=s.substring(s.length()-32,s.length());
}

int go=Integer.parseInt(s,2);
aa=(int)((aa+go)%val);
aa = (aa << sh[i]) | (aa >>> (32 - sh[i]));
aa=(int)((aa+bb)%val);
e=aa;
fa=bb;
g=cc;
h=dd;
bb=e;cc=fa;dd=g;aa=h;
}

aa=(int)((aa+ee)%val);
bb=(int)((bb+ff)%val);
cc=(int)((cc+gg)%val);
dd=(int)((dd+hh)%val);

}


System.out.println("Result of the md5 for the given file is "+aa+bb+cc+dd);
}
catch(Exception ex)
{
System.out.println(ex);
String s=ex.toString();
text.setText(s);
}

text.setText("Result after MD5 is    ");
try
{
String re;
re=Integer.toString(aa,10);
text.append(re);
re=Integer.toString(bb,10);
text.append(re);
re=Integer.toString(cc,10);
text.append(re);
re=Integer.toString(dd,10);
text.append(re);
re=Integer.toString(aa,10)+Integer.toString(bb,10)+Integer.toString(cc,10)+Integer.toString(dd,10);


f1=new File(str);
 FileReader fr5=new FileReader(f1);
 char[][] ar5=new char[2][1000000];
 int le5=(int)(f1.length());
 fr5.read(ar5[1],0,le5);
 String str5=new String(ar5[1]);
 str5=str5.trim();
 System.out.println(str5);
 fr5.close();
 BufferedWriter fw5 = new BufferedWriter(new FileWriter(str));
 fw5.write(str5);
 fw5.newLine();
 fw5.write(re);
 fw5.close();







Thread.sleep(2000);


text.setText("Click Encrypt to encrypt the data");

}
catch(Exception e){System.out.println(e);}
}
else if(s=="ENCRYPT")
{

l7.setBounds(590,400,100,30);
l8.setBounds(590,450,100,30);
text2.setBounds(720,400,100,30);
text3.setBounds(720,450,100,30);
b6.setBounds(650,500,100,30);
text.setText("Enter 8 character key and number of rounds, then submit");

}
else if(s=="SUBMIT")
{
JOptionPane.showMessageDialog(null, "USE THESE SAME KEYS AND NUMEBR OF ROUNDS IN RECEIVER SIDE.", "CIA", 1);

String ee=text2.getText();
String ee1=text3.getText();
text.setText("Values:   "+ ee +"  "+ ee1 + "  "+str);

nr nrr=new nr();
nrr.encry(ee,ee1,str);
text.setText("Encryption completed");
JOptionPane.showMessageDialog(null, "PROCESS COMPLETED", "CIA", 1);


try
{
File f2=new File("d:/e.txt");
FileReader fr=new FileReader(f2);
int le=(int)(f2.length());
fr.read(a[1],0,le);
sr=new String(a[1]);
fr.close();
}
catch(Exception eee)
{}
text.setText("DATA AFTER ENCRYPTION  " + "\n" +sr);




}
else if(s=="DECRYPT")
{
l6.setBounds(1055,130,200,30);
l5.setBounds(1055,180,200,30);
l4.setBounds(1055,230,200,30);
l4.setEnabled(false);
l5.setEnabled(false);
l6.setEnabled(false);


l7.setBounds(590,400,100,30);
l8.setBounds(590,450,100,30);
text2.setBounds(720,400,100,30);
text3.setBounds(720,450,100,30);
b7.setBounds(650,500,100,30);

text.setText("Enter 8 character key and number of rounds, then submit1");


}

else if(s=="SUBMIT1")
{

String ee=text2.getText();
String ee1=text3.getText();
text.setText("Values:   "+ ee +"  "+ ee1 + "  "+str);
try
{
nr1 nrr1=new nr1();
mdvv=nrr1.decry(ee,ee1);
text.setText("Decryption completed");
Thread.sleep(2000);
text.setText("Separated md5 value is   "+mdvv);
Thread.sleep(2000);
text.setText("CLICK DSTART TO CONTINUE THE PROCESS");
}
catch(Exception e4){}

}
else if(s=="DSTART")
{

mdd mddd=new mdd();
String mvalue=mddd.md1();
text.setText("Value of message digest is    "+mvalue);


try
{
Thread.sleep(3000);
System.out.println(mdvv);
System.out.println(mvalue);
mdvv=mdvv.trim();
mvalue=mvalue.trim();
if(mvalue.compareTo(mdvv) == 0)
{
 text.setText("DATA IS NOT MODIFIED DURING THE TRANSMISSION");
 JOptionPane.showMessageDialog(null, "DATA IS NOT MODIFIED DURING THE TRANSMISSION", "CIA", 1);
 }
else
{
 text.setText("DATA IS MODIFIED DURING THE TRANSMISSION");
 JOptionPane.showMessageDialog(null, "DATA IS MODIFIED DURING THE TRANSMISSION", "CIA", 1);

}



Thread.sleep(3000);}
catch(Exception e){}

vir2 vvv=new vir2();
int con=vvv.virus("d:/g.txt");
if(con == 1)
{
 text.setText("Virus found, necessary actions taken");
 JOptionPane.showMessageDialog(null, "VIRUS FOUND, NECESSARY ACTIONS TAKEN", "CIA", 1);
}
else
{
 text.setText("No virus found");
 JOptionPane.showMessageDialog(null, "NO VIRUS FOUND", "CIA", 1);
}

try
{
File f2=new File("d:/g.txt");
FileReader fr=new FileReader(f2);
int le=(int)(f2.length());
fr.read(a[1],0,le);
sr=new String(a[1]);
fr.close();
JOptionPane.showMessageDialog(null, "PROCESS COMPLETED", "CIA", 1);
}

catch(Exception ee)
{}

text.setText("ORIGINAL TEXT AFTER COMPILATION OF PROCESSES  " + "\n" +sr);

}

}
}

/*
class MyWindowAdapter extends WindowAdapter {
MenuFrame menuFrame;
public MyWindowAdapter(MenuFrame menuFrame) {
this.menuFrame = menuFrame;
}
public void windowClosing(WindowEvent we) {
menuFrame.setVisible(false);
}
}
*/

public class af2 extends JApplet {
MenuFrame f;
public void init() {
f = new MenuFrame("A Frame Window");
f.setSize(1366,600);
f.setVisible(true);
}
public void start() {
f.setVisible(true);
}
public void stop() {
f.setVisible(false);
}
public void paint(Graphics g) {
g.drawString("This is in applet window", 10, 20);
}
}



//ENCRYPTION





 class nr
{
 public void encry(String ee,String ee1,String finame)
{
BufferedReader br;
String key;
int round;
int[][] k=new int[100][8];
String vaa[]=new String[100];
long vaa1[]=new long[100];
String xx,r11,r22,sr;
long[] s;
long[] l;
int b, u, t, c,a1,b1,c1,d1,enn,le;
char[][] a=new char[2][1000000];
long r1,r2,x,y;
 long P32 = 3084996963L;
 long Q32 = 2654435769L;

try
{


 br = new BufferedReader(new InputStreamReader(System.in));
//System.out.println("Enter the key of exactly 8 character");
key=ee;
//System.out.println(key);
//System.out.println("enter the number of rounds");
round=Integer.parseInt(ee1);
//System.out.println(round);
lr ll = new lr();

//Generate key from String;

char[] mykeyinchar = key.toCharArray();
//System.out.println(mykeyinchar.length);
for (int i = 0; i < mykeyinchar.length; i++)
{
String val=Long.toBinaryString(mykeyinchar[i]);

int va=val.length();
int j=8-va;
for(int k1=0;k1<j;k1++)
{
 val='0'+val;
}
vaa[i]=val;
}

b=mykeyinchar.length;
u = 32/8;
t = (int)(2*(round+1));
c = b / u;
s = new long[t];
l = new long[c];


//Key Generation:
String key1[]=new String[2];
key1[0]=vaa[0]+vaa[1]+vaa[2]+vaa[3];
key1[1]=vaa[4]+vaa[5]+vaa[6]+vaa[7];
int jjj=0;


//System.out.println(key1[0]);
//System.out.println(key1[1]);

//System.out.println("division value  "+ 7/4);
l[0]=(long)(Long.parseLong(key1[0],2));
l[1]=(long)(Long.parseLong(key1[1],2));

for (int i = 0; i < mykeyinchar.length; i++)
{
  vaa1[i]=(long)(Long.parseLong(vaa[i],2));
  //System.out.println(vaa1[i]);
}


long val=4294967296L;
for (int i = mykeyinchar.length - 1; i >= 0; i--)
{
l[i/u]=(ll.left(l[i/u], 8)+vaa1[i])%val;
} 

System.out.println("values of L");
System.out.println(l[0]);
System.out.println(l[1]);


s[0] = P32;

for (int i = 1; i <= t - 1; i++)
{

s[i] = (s[i - 1] + Q32)%val;
}



int ii, jj;
ii = jj = 0;

x = y = 0;
int v = 3 * Math.max(t, c);
for (int counter = 0; counter <= v; counter++)
{

x = s[ii] = (ll.left((((s[ii] + x )%val)+ y)%val, 3))%val;
y = l[jj] = (ll.left((((l[jj] + x)%val) + y)%val, (long)((x + y)%val)))%val;

ii = (ii + 1) % t;
jj = (jj + 1) % c;
}

System.out.println("Keys of the alg");
for( ii=0;ii<t;ii++)
{
 
System.out.println(s[ii]);
}
 

 System.out.println("Encrypted data");
 
//Encode part

File ff=new File(finame);
BufferedReader brr = new BufferedReader(new FileReader(ff));
 String fin="D:/d.txt";
 BufferedWriter bw1 = new BufferedWriter(new FileWriter(fin,true));

while((c1 = brr.read()) != -1)
{


String si=Integer.toBinaryString(c1);
c1=si.length();
switch(c1)
{
case 0:
bw1.write("00000000");
break;
case 1:
bw1.write("0000000");
bw1.write(si);
break;
case 2:
bw1.write("000000");
bw1.write(si);
break;
case 3:
bw1.write("00000");
bw1.write(si);
break;
case 4:
bw1.write("0000");
bw1.write(si);
break;
case 5:
bw1.write("000");
bw1.write(si);
break;
case 6:
bw1.write("00");
bw1.write(si);
break;
case 7:
bw1.write("0");
bw1.write(si);
break;
case 8:
bw1.write(si);
break;
}
}


int len1=(int)ff.length();
System.out.println("length and modulo of the file    "+len1 + "   "+(len1*8)%64);
len1=(len1*8)%64;
if(len1==0)
len1=0;
else
len1=64-len1;
for(int z=0;z<len1;z++)
 bw1.write('0');

bw1.close();



 File f=new File("D:/d.txt");
  FileReader fr=new FileReader(f);
 
 File fin2=new File("D:/e.txt");
BufferedWriter bw = new BufferedWriter(new FileWriter(fin2));
  
  le=(int)(f.length());
  fr.read(a[1],0,le);
  sr=new String(a[1]);
enn=0;
for(int en=0;en<le/64;en++)
{  
a1=enn*32;
b1=a1+32;
c1=b1;
d1=b1+32;
enn=enn+2;




r11=sr.substring(a1,b1);
r22=sr.substring(c1,d1);

r1=(long)(Long.parseLong(r11,2));
r2=(long)(Long.parseLong(r22,2));

System.out.println(r1);
System.out.println(r2);


r1 = (r1 + s[0])%val;
System.out.println("r1  "+r1);
r2 = (r2+ s[1])%val;
System.out.println("r2  "+r2);
for (int i = 1; i <= round; i++)
{
r1 = (ll.left(r1 ^ r2, (long)r2) + s[2 * i])%val;
System.out.println("r1  "+r1);
r2 = (ll.left(r2 ^ r1, (long)r1) + s[2 * i + 1])%val;
System.out.println("r2  "+r2);
}



System.out.println("Value of r1  "+r1);
System.out.println("Value of r2  "+r2);

//System.out.println("Value of r1  "+Long.toString(r1));
//System.out.println("Value of r2  "+Long.toString(r2));

bw.write(Long.toString(r1));
bw.newLine();
//bw.write((char)13);
bw.write(Long.toString(r2));
bw.newLine();
//System.out.println(4 << 5);

}
bw.close();
}
catch(Exception e){System.out.println(e);}

}

}

class lr
{
public long left(long x1,long offset)
{

long t1, t2;
long val=4294967296L;

/*String x=Long.toBinaryString(x1);
//System.out.println(x);
int va=x.length();
if(offset < va  && x1 > 0)
{
 //System.out.println("inside  "+offset);
 int j=32-va;
for(int k1=0;k1<j;k1++)
{
x='0'+x;
}
t2 = (x1 << offset);
x=Long.toBinaryString(t2);
x=x.substring(x.length()-va,x.length());
t2=Long.parseLong(x,2);
} 
else if(x1 < 0)
 t2=x1 << offset;
else
 t2=0;

System.out.println("Value of t2  "+t2);*/
return (x1);
}

}




//VIRUS CHECK:




class vir2
{
 public int virus(String finame)
{
File f1;
FileReader f;
char a[][]=new char[4][100000];
int i,j,len,n,ii,fl,pp=0;
String s,str4=null;
String fname[]=new String[5];
 try
{
BufferedReader br1=new BufferedReader(new InputStreamReader(System.in));
//System.out.println("Enter the number of virus files");
fl=1;
//System.out.println("Enter the file names");
//for(i=0;i<fl;i++)
 //fname[i]=br1.readLine();
fname[0]="d:/wtext.txt";

f1=new File(finame);
f=new FileReader(f1);
j=0;
BufferedReader b=new BufferedReader(f);
while((s = b.readLine()) != null)
{
  len=s.length();
  a[0]=s.toCharArray();
  for(i=0;i<len;i++)
{
  if(a[0][i] != ' ') 
{
    a[2][j]=a[0][i];  
    j++;
}
}
  }
int m=j;
String str1=new String(a[2]);
str1=str1.trim();
b.close();




for(ii=0;ii<fl;ii++)
{
File f2=new File(fname[ii]);
FileReader r=new FileReader(f2);
j=0;
BufferedReader br=new BufferedReader(r);
while((s = br.readLine()) != null)
{
  len=s.length();
  a[0]=s.toCharArray();
  for(i=0;i<len;i++)
{
  if(a[0][i] != ' ') 
{
    a[3][j]=a[0][i];  
    j++;
}
}
  
}
a[3][j]='\0';
n=j;
br.close();
System.out.println("The length of the  file 1 is" + m);
System.out.println("The length of the   file 2 is " + n);


String str2=new String(a[3]);
//System.out.println(str1.contentEquals(str2));
str2=str2.trim();
str2=str2.substring(0,n);
//System.out.println(str2);


int p=0;
for(i=0;i<=(m-n);i++)
{
String ss=str1.substring(i,(n)+i);
if(ss.compareTo(str2) == 0)
 {
p=1;
j=i;
i=m;

}  
}

if(p==1)
{

File fff=new File(finame);
FileWriter ffw=new FileWriter(fff);

 System.out.println(fname[ii]+" virus found");
 pp=1; 
String ss1=str1.substring(0,j);
System.out.println(ss1);
String str5=str1.substring(n+j,m);
System.out.println(str5);
 str4=ss1+str5;
System.out.println("File without virus is");
System.out.println(str4);
ffw.write(str4);
ffw.close();


}

else
  System.out.println(fname[ii]+" Virus not found");
}




//ss1=str1;
//str5=str1;
for(ii=0;ii<fl;ii++)
{
 
File f2=new File(fname[ii]);
FileReader r=new FileReader(f2);
j=0;
BufferedReader br=new BufferedReader(r);

while((s = br.readLine()) != null)
{
 
 a[0]=s.toCharArray();
int rr=0;
 n=s.length();

  for(int q=0;q<n;q++)
{
  if(a[0][q] != ' ') 
{
    a[3][rr]=a[0][q];  
    rr++;
}
}

String s2=new String(a[3]);
s2=s2.substring(0,rr);
s2=s2.trim();
n=s2.length();
//System.out.println(s2);
//System.out.println(n);
int p=pp=0;
m=str1.length();
for(i=0;i<=(m-n);i++)
{
String ss=str1.substring(i,n+i);
if(ss.compareTo(s2) == 0)
{
p=1;
j=i;
i=m;
}
}
if(p==1)
{
File fff=new File(finame);
FileWriter ffw=new FileWriter(fff);

pp=1;
String ss1=str1.substring(0,j);
//System.out.println(ss1);
String str5=str1.substring(n+j,m);
//System.out.println(str5);
//str1=null;
ss1=ss1.trim();
str5=str5.trim();
str4=ss1+str5;
//System.out.println(str4);
str1=str4;
ffw.write(str1);
ffw.close();
}
s=null;
} 
}
System.out.println("original data after virus check  "+ str1);
}
catch(Exception e){
System.out.println(e);
}
return(pp);
}
}


//DECRYPTION:




class nr1
{
 public String decry(String ee,String ee1)
{
BufferedReader br;
String key;
int round;
int[][] k=new int[100][8];
String vaa[]=new String[100];
long vaa1[]=new long[100];
String xx,r11,r22,sr,str,mdv;
long[] s;
long[] l;
int b, u, t, c,a1,b1,c1,d1,enn,le,len;
char[][] a=new char[2][1000000];
long r1,r2,x,y;
 long P32 = 3084996963L;
 long Q32 = 2654435769L;

try
{


 br = new BufferedReader(new InputStreamReader(System.in));
//System.out.println("Enter the key of exactly 8 character");
key=ee;
//System.out.println(key);
//System.out.println("enter the number of rounds");
round=Integer.parseInt(ee1);
//System.out.println(round);
llr ll = new llr();

//Generate key from String;

char[] mykeyinchar = key.toCharArray();
//System.out.println(mykeyinchar.length);
for (int i = 0; i < mykeyinchar.length; i++)
{
String val=Long.toBinaryString(mykeyinchar[i]);

int va=val.length();
int j=8-va;
for(int k1=0;k1<j;k1++)
{
 val='0'+val;
}
vaa[i]=val;
}

b=mykeyinchar.length;
u = 32/8;
t = (int)(2*(round+1));
c = b / u;
s = new long[t];
l = new long[c];


//Key Generation:
String key1[]=new String[2];

key1[0]=vaa[0]+vaa[1]+vaa[2]+vaa[3];
key1[1]=vaa[4]+vaa[5]+vaa[6]+vaa[7];

//System.out.println(key1[0]);
//System.out.println(key1[1]);

//System.out.println("division value  "+ 7/4);
l[0]=(long)(Long.parseLong(key1[0],2));
l[1]=(long)(Long.parseLong(key1[1],2));

for (int i = 0; i < mykeyinchar.length; i++)
{
  vaa1[i]=(long)(Long.parseLong(vaa[i],2));
  //System.out.println(vaa1[i]);
}


long val=4294967296L;
for (int i = mykeyinchar.length - 1; i >= 0; i--)
{
l[i/u]=(ll.left(l[i/u], 8)+vaa1[i])%val;
} 

System.out.println("values of L");
System.out.println(l[0]);
System.out.println(l[1]);


s[0] = P32;

for (int i = 1; i <= t - 1; i++)
{

s[i] = (s[i - 1] + Q32)%val;
}



int ii, jj;
ii = jj = 0;

x = y = 0;
int v = 3 * Math.max(t, c);
for (int counter = 0; counter <= v; counter++)
{
x = s[ii] = (ll.left((((s[ii] + x )%val)+ y)%val, 3))%val;
y = l[jj] = (ll.left((((l[jj] + x)%val) + y)%val, (long)((x + y)%val)))%val;

ii = (ii + 1) % t;
jj = (jj + 1) % c;
}

System.out.println("Keys of the alg");
for( ii=0;ii<t;ii++)
{
 
 System.out.println(s[ii]);
}
 

 System.out.println("Decrypted data");
 
//Decode part


 File f=new File("d:/e.txt");
  FileReader fr=new FileReader(f);
  BufferedReader br1 = new BufferedReader(fr);
 
 File fin=new File("D:/f.txt");
 BufferedWriter bw = new BufferedWriter(new FileWriter(fin));
  
/*  le=(int)(f.length());
  fr.read(a[1],0,le);
  sr=new String(a[1]);
enn=0;*/
File f1=new File("D:/d.txt");
le=(int)(f1.length());
le=le/64; 
for(int en=0;en<le;en++)
{  
/*
a1=enn*32;
b1=a1+32;
c1=b1;
d1=b1+32;
enn=enn+2;
*/



r11=br1.readLine();
r22=br1.readLine();
r11=r11.trim();
r22=r22.trim();

r1=(long)(Long.parseLong(r11));
r2=(long)(Long.parseLong(r22));

System.out.println(r1);
System.out.println(r2);
//r1=2757524830L;
//r2=855258136;
for (int i = round; i >= 1; i--)
{

r2 = ((ll.right(r2 - s[2 * i + 1], (long)r1)) ^ r1);

r1 = ((ll.right(r1 - s[2 * i], (long)r2)) ^ r2);

}


r2 = (r2 - s[1]);
r1 = (r1 - s[0]);

System.out.println(r1);
System.out.println(r2);

long va2=9223372036854775807L;

xx=Long.toBinaryString(r1);
int va=xx.length();
int j=64-va;
for(int k1=0;k1<j;k1++)
{
 xx='0'+xx;
}

System.out.println(" r1  "+xx);
xx=xx.substring(32,64);
bw.write(xx);
r1=Long.parseLong(xx,2);
System.out.println("Value of r1  "+r1);

 xx=Long.toBinaryString(r2);
 va=xx.length();
 j=64-va;
for(int k1=0;k1<j;k1++)
{
 xx='0'+xx;
}
System.out.println(" r2  "+xx);
xx=xx.substring(32,64);
r2=Long.parseLong(xx,2);
System.out.println("Value of r2  "+r2);

//System.out.println("Value of r1  "+Long.toString(r1));
//System.out.println("Value of r2  "+Long.toString(r2));

bw.write(xx);
}
bw.close();

//binary to string:



  File fi=new File("D:/f.txt");
  FileReader fr1=new FileReader(fi);
  //File f1=new File("D:/files/e.txt");
  //FileWriter fw=new FileWriter(f1);
String fin1="D:/g.txt";
OutputStream bw2 = new FileOutputStream(fin1);
 
   le=(int)(fi.length());
  fr1.read(a[1],0,le);
  sr=new String(a[1]);
  int i1=1;
  int j1=i1+7;
  for(len=0;len<le/8;len++)
  {
   str=sr.substring(i1,j1);
   //System.out.println(str);
   i1=j1+1;
   j1=i1+7;   
   //Binary to Decimal 

  //BufferedReader bf= new BufferedReader(new InputStreamReader(System.in));
  //System.out.print("Enter the Binary value: ");
  //String str = bf.readLine();
  long num = Long.parseLong(str);
  long rem;
  while(num > 0)
  {
  rem = num % 10;
  num = num / 10;
  if(rem != 0 && rem != 1)
  {
  System.out.println("This is not a binary number.");
  System.out.println("Please try once again.");
  System.exit(0);
  }
  }
  int i= Integer.parseInt(str,2);
  //System.out.println("Decimal:="+ i);

  //Decimal to ASCII

  char c2 = (char) i ;
  bw2.write(i);
  System.out.print( c2 );
  }
 bw2.close();

 mdv="0";
 File f5=new File("D:/g.txt");
  
 fr=new FileReader(f5);
 br1 = new BufferedReader(fr);
 String s5=new String();
 int i7,i5=0;
 while((s5 = br1.readLine()) != null)
 i5++;
 br1.close();
 System.out.println("Number of lines   "+i5);
 i7=0;
f5=new File("D:/g.txt");
fr=new FileReader(f5);
 br1 = new BufferedReader(fr);
 while((s5 = br1.readLine()) != null)
 {
   if(i7 == i5-1)
   {
     mdv=s5;
    }
  i7++;
  }
 System.out.println(mdv);
 br1.close(); 


 int len6=mdv.length();
 File f6=new File("D:/g.txt");
 FileReader fr5=new FileReader(f6);
 char[][] ar5=new char[2][1000000];
 int le5=(int)(f6.length());
 fr5.read(ar5[1],0,le5);
 String str5=new String(ar5[1]);
 str5=str5.trim();
 System.out.println(str5);
 fr5.close();
  
 str5=str5.substring(0,str5.length()-len6);
 str5=str5.trim();
 BufferedWriter fw5 = new BufferedWriter(new FileWriter("D:/g.txt"));
 fw5.write(str5);
 fw5.close();
 
 
 }

catch(Exception e){System.out.println(e);
mdv="0";}
return(mdv);
}
}

class llr
{


public long left(long x1,long offset)
{

long t1, t2;
long val=4294967296L;

/*String x=Long.toBinaryString(x1);
int va=x.length();
if(offset < va  && x1 > 0)
{
 
 int j=32-va;
for(int k1=0;k1<j;k1++)
{
x='0'+x;
}
t2 = (x1 << offset);
x=Long.toBinaryString(t2);
x=x.substring(x.length()-va,x.length());
t2=Long.parseLong(x,2);
} 
else if(x1 < 0)
 t2=x1 << offset;
else
 t2=0;
*/ 

//System.out.println("Value of t2  "+t2);
return (x1);

}




public long right(long x1,long offset)
{

long t1, t2;
long val=4294967296L;

String x=Long.toBinaryString(x1);
int va=x.length();
/*if(offset < va  && x1 > 0)
{
 
 int j=32-va;
for(int k1=0;k1<j;k1++)
{
x='0'+x;
}
t2 = (x1 >> offset);
x=Long.toBinaryString(t2);
x=x.substring(0,va);
t2=Long.parseLong(x,2);
} 
else if(x1 < 0)
 t2=x1 >> offset;
else
 t2=0;

System.out.println("Value of t2  "+t2);*/
return (x1);

}


}



//Md5 on Decryprion side




class mdd
{
 public String md1()
{
 File f1,f2;
 String s,st;  
  long  n,m,len;
 int a,i,k,mo;
 int c;
//String buf[],aa,bb,cc,dd;
int aa,bb,cc,dd,ee,ff,gg,hh,e,fa,h,g;
//buf = new String[4];
int buf[],t[];
buf = new int[4];
int sh[]=new int[65];
t=new int[65];
		// Initialising MD buffer
		/*buf[0] = "67452301";
		buf[1] = "efcdab89";
		buf[2] = "98badcfe";
		buf[3] = "10325476";*/


                              buf[0] = 0x67452301;
		buf[1] = 0xefcdab89;
		buf[2] = 0x98badcfe;
		buf[3] = 0x10325476;

t[1]=0xd76aa478; t[2]=0xe8c7b756; t[3]=0x242070db; t[4]=0xc1bdceee; t[5]=0xf57c0faf; t[6]=0x4787c62a; t[7]=0xa8304613; t[8]=0xfd469501; 
t[9]=0x698098d8; t[10]=0x8b44f7af; t[11]=0xffff5bb1;t[12]=0x895cd7be; t[13]=0x6b901122; t[14]=0xfd987193; t[15]=0xa679438e; t[16]=0x49b40821; 
t[17]=0xf61e2562; t[18]=0xc040b340; t[19]=0x265e5a51; t[20]=0xe9b6c7aa; t[21]=0xd62f105d; t[22]=0x02441453; t[23]=0xd8a1e681; t[24]=0xe7d3fbc8; 
t[25]=0x21e1cde6; t[26]=0xc33707d6; t[27]=0xf4d50d87; t[28]=0x455a14ed; t[29]=0xa9e3e905; t[30]=0xfcefa3f8; t[31]=0x676f02d9; t[32]=0x8d2a4c8a; 
t[33]=0xfffa3942; t[34]=0x8771f681; t[35]=0x699d6122; t[36]=0xfde5380c; t[37]=0xa4beea44; t[38]=0x4bdecfa9; t[39]=0xf6bb4b60; t[40]=0xbebfbc70; 
t[41]=0x289b7ec6; t[42]=0xeaa127fa; t[43]=0xd4ef3085; t[44]=0x04881d05; t[45]=0xd9d4d039; t[46]=0xe6db99e5; t[47]=0x1fa27c78; t[48]=0xc4ac5665; 
t[49]=0xf4292244; t[50]=0x432aff97; t[51]=0xab9423a7; t[52]=0xfc93a039; t[53]=0x655b59c3; t[54]=0x8f0ccc92; t[55]=0xffeff47d; t[56]=0x85845dd1; 
t[57]=0x6fa87e4f; t[58]=0xfe2ce6e0; t[59]=0xa3014314; t[60]=0x4e0811a1; t[61]=0xf7537e82; t[62]=0xbd3af235; t[63]=0x2ad7d2bb; t[64]=0xeb86d391;

sh[1]=7 ;  sh[2]=12 ; sh[3]=17 ; sh[4]=22 ;  sh[5]=7 ;  sh[6]=12 ;  sh[7]=17 ;  sh[8]=22 ;
sh[9]=7 ;  sh[10]= 12; sh[11]=17 ; sh[12]=22 ;  sh[13]=7 ;  sh[14]=12 ;  sh[15]=17 ;  sh[16]=22 ;
sh[17]= 5;  sh[18]= 9; sh[19]= 14; sh[20]=20 ;  sh[21]=5 ;  sh[22]=9 ;  sh[23]=14 ;  sh[24]=20 ;
sh[25]=5 ;  sh[26]= 9; sh[27]= 14; sh[28]=20 ;  sh[29]= 5;  sh[30]=9 ;  sh[31]=14 ;  sh[32]=20 ;
sh[33]=4 ;  sh[34]=11 ; sh[35]=16 ; sh[36]=23 ;  sh[37]=4 ;  sh[38]=11 ;  sh[39]=16 ;  sh[40]=23 ;
sh[41]=4 ;  sh[42]=11 ; sh[43]=16 ; sh[44]=23 ;  sh[45]=4 ;  sh[46]=11 ;  sh[47]=16 ;  sh[48]=23 ;
sh[49]= 6;  sh[50]=10 ; sh[51]=15 ; sh[52]=21 ;  sh[53]=6 ;  sh[54]=10 ;  sh[55]=15 ;  sh[56]=21 ;
sh[57]=6 ;  sh[58]=10 ; sh[59]=15 ; sh[60]= 21;  sh[61]=6 ;  sh[62]=10 ;  sh[63]=15 ;  sh[64]=21 ; 


/*
String t[]=new String[65];
t[1]="d76aa478"; t[2]="e8c7b756"; t[3]="242070db"; t[4]="c1bdceee"; t[5]="f57c0faf"; t[6]="4787c62a"; t[7]="a8304613"; t[8]="fd469501"; 
t[9]="698098d8"; t[10]="8b44f7af"; t[11]="ffff5bb1";t[12]="895cd7be"; t[13]="6b901122"; t[14]="fd987193"; t[15]="a679438e"; t[16]="49b40821"; 
t[17]="f61e2562"; t[18]="c040b340"; t[19]="265e5a51"; t[20]="e9b6c7aa"; t[21]="d62f105d"; t[22]="02441453"; t[23]="d8a1e681"; t[24]="e7d3fbc8"; 
t[25]="21e1cde6"; t[26]="c33707d6"; t[27]="f4d50d87"; t[28]="455a14ed"; t[29]="a9e3e905"; t[30]="fcefa3f8"; t[31]="676f02d9"; t[32]="8d2a4c8a"; 
t[33]="fffa3942"; t[34]="8771f681"; t[35]="699d6122"; t[36]="fde5380c"; t[37]="a4beea44"; t[38]="4bdecfa9"; t[39]="f6bb4b60"; t[40]="bebfbc70"; 
t[41]="289b7ec6"; t[42]="eaa127fa"; t[43]="d4ef3085"; t[44]="04881d05"; t[45]="d9d4d039"; t[46]="e6db99e5"; t[47]="1fa27c78"; t[48]="c4ac5665"; 
t[49]="f4292244"; t[50]="432aff97"; t[51]="ab9423a7"; t[52]="fc93a039"; t[53]="655b59c3"; t[54]="8f0ccc92"; t[55]="ffeff47d"; t[56]="85845dd1"; 
t[57]="6fa87e4f"; t[58]="fe2ce6e0"; t[59]="a3014314"; t[60]="4e0811a1"; t[61]="f7537e82"; t[62]="bd3af235"; t[63]="2ad7d2bb"; t[64]="eb86d391";
*/



 try
{


 f1=new File("D:/g.txt");
 FileReader fr=new FileReader(f1);
 char[][] ar5=new char[2][1000000];
 int le5=(int)(f1.length());
 fr.read(ar5[1],0,le5);
 String str5=new String(ar5[1]);
 str5=str5.trim();
 System.out.println(str5);
 fr.close();
 FileWriter fw5=new FileWriter(f1);
 fw5.write(str5);
 fw5.close();

 

 f2=new File("D:/h.txt");
 fr=new FileReader(f1);
 FileWriter fw=new FileWriter(f2);
 BufferedReader br = new BufferedReader(fr);
 len=(int)f1.length();
 System.out.println("Length of the given file is"+len);


while((c = fr.read()) != -1)
{
if(c<58 && c>47)
{
 c=c-48;
}
s=Integer.toBinaryString(c);
c=s.length();
switch(c)
{
case 0:
fw.write("00000000");
break;
case 1:
fw.write("0000000");
fw.write(s);
break;
case 2:
fw.write("000000");
fw.write(s);
break;
case 3:
fw.write("00000");
fw.write(s);
break;
case 4:
fw.write("0000");
fw.write(s);
break;
case 5:
fw.write("000");
fw.write(s);
break;
case 6:
fw.write("00");
fw.write(s);
break;
case 7:
fw.write("0");
fw.write(s);
break;
case 8:
fw.write(s);
break;
}
}
//fr.close();
//fw.close();



n=f2.length();
System.out.println(n);

s=null;
//APPEND PADDING BITS AND LENGTH:
if((len*8) < 448)
{
 m=448-(len*8);
 fw.write("1");
 for(i=0;i<m-1;i++)
 { 
   fw.write("0");
 }
System.out.println("Length of the test1 file is"+f2.length());
System.out.println("Binary equivalent of the "+len+" is " +Integer.toBinaryString((int)len));
s=Integer.toBinaryString((int)len);
m=s.length();
System.out.println("Length of the length"+m);
m=64-m;
for(i=0;i<m;i++)
{ 
   fw.write("0");
 }
fw.write(s);
fr.close();
fw.close();
System.out.println("Length of the test1 file is"+f2.length());
}
else
{
m=(len*8)%512;
if(m<448)
{

 m=448-m;
 fw.write("1");
 for(i=0;i<m-1;i++)
 { 
   fw.write("0");
 }
System.out.println("Length of the test1 file is"+f2.length());
System.out.println("Binary equivalent of the "+len+" is " +Integer.toBinaryString((int)len));
s=Integer.toBinaryString((int)len);
m=s.length();
System.out.println("Length of the length"+m);
m=64-m;
 for(i=0;i<m;i++)
 { 
   fw.write("0");
 }
fw.write(s);
fr.close();
fw.close();
System.out.println("Length of the test1 file is"+f2.length());
}
else if(m>=448)
{

m=512-m;
fw.write("1");
for(i=0;i<m+447;i++)
{
fw.write("0");
}
System.out.println("Binary equivalent of the "+len+" is " +Integer.toBinaryString((int)len));
s=Integer.toBinaryString((int)len);
m=s.length();
System.out.println("Length of the length"+m);
m=64-m;
 for(i=0;i<m;i++)
 { 
   fw.write("0");
 }
fw.write(s);
fr.close();
fw.close();
System.out.println("Length of the test1 file is"+f2.length());
}
}
//processing of 512 block

aa=buf[0];
bb=buf[1];
cc=buf[2];
dd=buf[3];


double val=Math.pow(2,32);
//System.out.println(val);
fr=new FileReader(f2);

char[][] ar=new char[2][1000000];
int le=(int)(f2.length());
fr.read(ar[1],0,le);
String str=new String(ar[1]);
//System.out.println(st);
len=f2.length();
System.out.println(len);
len=len/512;
System.out.println(len);

k=1;
mo=0;
int flag;
flag=0;
for(int count=0;count<len;count++)
{

ee=aa;
ff=bb;
gg=cc;
hh=dd;


int flen=count*512;
int flen1=flen+512;

st=str.substring(flen,flen1);

k=1;
mo=0;
//System.out.println("Before start of the round");

//Round 1:

for(i=1;i<17;i++)
{
aa = (int)( (aa+ ((bb & cc) | (~bb & dd)) ) % val);
aa=(int)((aa+t[i])%val);
int mod=mo*32;
int ko=k*32;
mo++;
k++;
s=st.substring(mod,ko);
if((long)Long.parseLong(s,2) >  2147483647)
{
  long lon=(long)Long.parseLong(s,2)% 2147483647L;
  s=Long.toBinaryString(lon);
  int valu=s.length();
int jnn=32-valu;
for(int k1=0;k1<jnn;k1++)
{
 s='0'+s;
}
  s=s.substring(s.length()-32,s.length());
}
  
//System.out.println("before go");
int go=Integer.parseInt(s,2);
aa=(int)((aa+go)%val);
aa = (aa << sh[i]) | (aa >>> (32 - sh[i]));
aa=(int)((aa+bb)%val);
e=aa;
fa=bb;
g=cc;
h=dd;
bb=e;cc=fa;dd=g;aa=h;
}
//System.out.println("After round 1");

//Round 2:

int j=0;
for(i=17;i<33;i++)
{
aa =(int)((aa+ ((bb & dd) | (cc & ~dd)))%val);
aa=(int)((aa+t[i])%val);
int mod=((1+(5*j))%16)*32;
int ko=mod+32;
j++;
s=st.substring(mod,ko);
if((long)Long.parseLong(s,2) >  2147483647)
{
  long lon=(long)Long.parseLong(s,2)% 2147483647L;
  s=Long.toBinaryString(lon);
  int valu=s.length();
int jnn=32-valu;
for(int k1=0;k1<jnn;k1++)
{
 s='0'+s;
}
  s=s.substring(s.length()-32,s.length());
}

int go=Integer.parseInt(s,2);
aa=(int)((aa+go)%val);
aa = (aa << sh[i]) | (aa >>> (32 - sh[i]));
aa=(int)((aa+bb)%val);
e=aa;
fa=bb;
g=cc;
h=dd;
bb=e;cc=fa;dd=g;aa=h;
}

//System.out.println("After round 2");
//Round 3:

 j=0;
for(i=33;i<49;i++)
{
aa = (int)((bb ^ cc ^ dd)%val);
aa=(int)((aa+t[i])%val);
int mod=((5+(3*j))%16)*32;
int ko=mod+32;
j++;
s=st.substring(mod,ko);
if((long)Long.parseLong(s,2) >  2147483647)
{
  long lon=(long)Long.parseLong(s,2)% 2147483647L;
  s=Long.toBinaryString(lon);
  int valu=s.length();
int jnn=32-valu;
for(int k1=0;k1<jnn;k1++)
{
 s='0'+s;
}
  s=s.substring(s.length()-32,s.length());
}

int go=Integer.parseInt(s,2);
aa=(int)((aa+go)%val);
aa = (aa << sh[i]) | (aa >>> (32 - sh[i]));
aa=(int)((aa+bb)%val);
e=aa;
fa=bb;
g=cc;
h=dd;
bb=e;cc=fa;dd=g;aa=h;
}

//System.out.println("After round 3");
//Round 4:

j=0;
for(i=49;i<=64;i++)
{
aa =(int)((aa+ (cc ^ (bb | ~dd)))%val);
aa=(int)((aa+t[i])%val);
int mod=((7*j)%16)*32;
int ko=mod+32;
j++;
s=st.substring(mod,ko);
if((long)Long.parseLong(s,2) >  2147483647)
{
  long lon=(long)Long.parseLong(s,2)% 2147483647L;
  s=Long.toBinaryString(lon);
  int valu=s.length();
int jnn=32-valu;
for(int k1=0;k1<jnn;k1++)
{
 s='0'+s;
}
  s=s.substring(s.length()-32,s.length());
}

int go=Integer.parseInt(s,2);
aa=(int)((aa+go)%val);
aa = (aa << sh[i]) | (aa >>> (32 - sh[i]));
aa=(int)((aa+bb)%val);
e=aa;
fa=bb;
g=cc;
h=dd;
bb=e;cc=fa;dd=g;aa=h;
}

//System.out.println("After round 4");
aa=(int)((aa+ee)%val);
bb=(int)((bb+ff)%val);
cc=(int)((cc+gg)%val);
dd=(int)((dd+hh)%val);



}
System.out.println("Completed");
 st=Integer.toString(aa);
System.out.println("aa  "+st);
String bbb=Integer.toString(bb);
System.out.println("bb  "+bbb);
String cbb=Integer.toString(cc);
System.out.println("cc  "+cbb);
String dbb=Integer.toString(dd);
System.out.println("dd  "+dbb);
st=st+bbb+cbb+dbb;
System.out.println("Result of the md5 for the given file is"+aa+bb+cc+dd);
}
catch(Exception eee){
System.out.println(eee);
st="0";
}

return st;

}
}


Code for virus dictionary (concept of anti virus).

import java.io.*;
class vir2
{
 public static void main(String args[])
{
File f1;
FileReader f;
char a[][]=new char[4][100000];
int i,j,len,n,ii,fl;
String s,str4=null;
String fname[]=new String[5];
 try
{
BufferedReader br1=new BufferedReader(new InputStreamReader(System.in));
System.out.println("Enter the number of virus files");
fl=Integer.parseInt(br1.readLine());
System.out.println("Enter the file names");
for(i=0;i<fl;i++)
 fname[i]=br1.readLine();

f1=new File("D:/files/test1.txt");
f=new FileReader(f1);
j=0;
BufferedReader b=new BufferedReader(f);
while((s = b.readLine()) != null)
{
  len=s.length();
  a[0]=s.toCharArray();
  for(i=0;i<len;i++)
{
  if(a[0][i] != ' ') 
{
    a[2][j]=a[0][i];  
    j++;
}
}
  }
int m=j;
String str1=new String(a[2]);
str1=str1.trim();




for(ii=0;ii<fl;ii++)
{
File f2=new File(fname[ii]);
FileReader r=new FileReader(f2);
j=0;
BufferedReader br=new BufferedReader(r);
while((s = br.readLine()) != null)
{
  len=s.length();
  a[0]=s.toCharArray();
  for(i=0;i<len;i++)
{
  if(a[0][i] != ' ') 
{
    a[3][j]=a[0][i];  
    j++;
}
}
  
}
a[3][j]='\0';
n=j;
System.out.println("The length of the  file 1 is" + m);
System.out.println("The length of the   file 2 is " + n);


String str2=new String(a[3]);
//System.out.println(str1.contentEquals(str2));
str2=str2.trim();
str2=str2.substring(0,n);
//System.out.println(str2);


int p=0;
for(i=0;i<=(m-n);i++)
{
String ss=str1.substring(i,(n)+i);
if(ss.compareTo(str2) == 0)
 {
p=1;
j=i;
i=m;

}  
}

if(p==1)
{
 System.out.println(fname[ii]+" virus found");
  
String ss1=str1.substring(0,j);
System.out.println(ss1);
String str5=str1.substring(n+j,m);
System.out.println(str5);
 str4=ss1+str5;
System.out.println("File without virus is");
System.out.println(str4);

}

else
  System.out.println(fname[ii]+" Virus not found");
}




//ss1=str1;
//str5=str1;
for(ii=0;ii<fl;ii++)
{
 
File f2=new File(fname[ii]);
FileReader r=new FileReader(f2);
j=0;
BufferedReader br=new BufferedReader(r);

while((s = br.readLine()) != null)
{
 
 a[0]=s.toCharArray();
int rr=0;
 n=s.length();

  for(int q=0;q<n;q++)
{
  if(a[0][q] != ' ') 
{
    a[3][rr]=a[0][q];  
    rr++;
}
}

String s2=new String(a[3]);
s2=s2.substring(0,rr);
s2=s2.trim();
n=s2.length();
//System.out.println(s2);
//System.out.println(n);
int p=0;
m=str1.length();
for(i=0;i<=(m-n);i++)
{
String ss=str1.substring(i,n+i);
if(ss.compareTo(s2) == 0)
{
p=1;
j=i;
i=m;
}
}
if(p==1)
{
String ss1=str1.substring(0,j);
//System.out.println(ss1);
String str5=str1.substring(n+j,m);
//System.out.println(str5);
//str1=null;
ss1=ss1.trim();
str5=str5.trim();
str4=ss1+str5;
//System.out.println(str4);
str1=str4;
}
s=null;
} 
}
System.out.println("original data after virus check  "+ str1);
}
catch(Exception e){
System.out.println(e);
}
}
}
