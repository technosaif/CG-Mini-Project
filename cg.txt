#include<GL/glut.h>
#include <string.h>
float dis = 0.0, tr = 0.0, tr1 = 0.0, tr2 = 0.0, tr3 = 0.0, tr4 = 0.0, tr5 = 0.0, tr6 = 0.0, tr7 = 0.0;
float tr8 = 0.0, tr9 = 0.0, tr10 = 0.0, tr11 = 0.0, tr12 = 0.0;
int cy_flag = 0, cy_flag1 = 0, cy_flag2 = 0;
int flag = 0, flag1 = 0, flag2 = 0, flag3 = 0, flag4 = 0, flag5 = 0;
int blink_flag = 0, blink_flag2 = 0;
float dis1 = 0;
float dis2 = 0;
float cy_height_1 = -0.1;
float cy_height_2 = -0.1;
float cy_height_3 = -0.1;
float cy_height_3_1 = -0.1;
float cy_height_4 = -0.1;
float con_blend = 0.0;
int connec = 0, hub1 = 0;
float Hub_R = 0, Hub_G = 4;

float c1r = -0.9, c1g = -0.9, c1b = 0.9;
float c2r = -0.9, c2g = -0.9, c2b = 0.9;
float c3r = -0.9, c3g = -0.9, c3b = 0.9;
float c4r = -0.9, c4g = -0.9, c4b = 0.9;

void anim();

void Cylinder(float cy_height)
{
	static GLUquadricObj* q;
	q = gluNewQuadric();
	gluQuadricNormals(q, GLU_TRUE);
	gluQuadricTexture(q, GLU_TRUE);
	gluCylinder(q, 0.4, 0.4, cy_height, 20, 20);
}

void computer(float scr, float scg, float scb)
{
	//////////////////Screen//////////////////////
	glScalef(1, 1, 0.3);

	//glColor4f(-3.0,-3.0,-3,1);
	glLineWidth(5);
	//glColor4f(-0.9,-0.9,0.9,0.8);
	glColor4f(scr - 2, scg - 2, scb - 2, 0.8);
	glutSolidCube(9.7);
	glScalef(1.4, 1.4, 1);


	////////////////Border///////////////////
	glColor4f(0.5, 0.5, 0.5, 1.8);
	glPushMatrix();//Bottom
	glTranslatef(0, -3.9, 0);
	glScalef(2.8, 0.3, 1);
	glutSolidCube(3);
	glPopMatrix();


	glPushMatrix(); //Left
	glTranslatef(-3.9, -0.18, 0);
	glScalef(0.3, 2.8, 1);
	glutSolidCube(3);
	glPopMatrix();

	glPushMatrix();//Top
	glTranslatef(-0.16, 3.9, 0);
	glScalef(2.8, 0.3, 1);
	glutSolidCube(3);
	glPopMatrix();

	glPushMatrix(); //Right
	glTranslatef(3.9, -0.0, 0);
	glScalef(0.3, 2.9, 1);
	glutSolidCube(3);
	glPopMatrix();


	//////////////////Stand/////////////////////////
	glColor4f(0.1, 0.1, 0.1, 1.8);
	glPushMatrix();
	glTranslatef(0, -5.3, 0);
	glScalef(1, 0.5, 1);
	glutSolidCube(3);
	glPopMatrix();


	////////////////////Keyboard////////////////////
	glColor4f(-0.1, -0.1, -0.1, 0.8);
	glPushMatrix();
	glTranslatef(0.5, -7.3, 0);
	glScalef(9, 0.6, 20.5);
	glutSolidCube(1);
	glColor4f(0.6, 0.6, 0.6, 0.8);
	glutWireCube(1);
	glPopMatrix();


	////////////////////Keys////////////////////
	glColor4f(4.9, 4.9, 4.9, 1.8);

	glBegin(GL_LINE_STRIP);
	glVertex3f(4.5, -7.5, 0);
	glVertex3f(-3.0, -7.5, 0);
	glVertex3f(-3.0, -7.5, -3);
	glVertex3f(4.5, -7.5, -3);
	glVertex3f(4.5, -7.5, -6);
	glVertex3f(-3.0, -7.5, -6);
	glVertex3f(-3.0, -7.5, -9);
	glVertex3f(4.5, -7.5, -9);
	glVertex3f(4.5, -7.5, -12);
	glVertex3f(-3.0, -7.5, -12);
	glVertex3f(-3.0, -7.5, 0);
	glVertex3f(-2.0, -7.5, 0);
	glVertex3f(-2.0, -7.5, -12);
	glVertex3f(-2.0, -7.5, -12);
	glVertex3f(-2.0, -7.5, 0);
	glVertex3f(-1.0, -7.5, 0);
	glVertex3f(-1.0, -7.5, -12);
	glVertex3f(-0.0, -7.5, -12);
	glVertex3f(-0.0, -7.5, 0);
	glVertex3f(1.0, -7.5, 0);
	glVertex3f(1.0, -7.5, -12);
	glVertex3f(2.0, -7.5, -12);
	glVertex3f(2.0, -7.5, 0);
	glVertex3f(3.0, -7.5, 0);
	glVertex3f(3.0, -7.5, -12);
	glVertex3f(4.0, -7.5, -12);
	glVertex3f(4.0, -7.5, 0);
	glVertex3f(4.5, -7.5, 0);
	glVertex3f(4.5, -7.5, -12);
	glEnd();
}
void cpu()
{
	//Desig of The CPU 
	glColor4f(0.0, 0.0, 0.0, 1.9);
	//cabinet
	glPushMatrix();
	glScalef(0.3, 1, 1);
	glTranslatef(-33, -3.3, 0);
	glutSolidCube(15);
	glColor4f(1.5, 0.0, 0.0, 1.9);
	glutWireCube(15);//for cpu red color outline
	glPopMatrix();
	//power bottom outer
	glPushMatrix();
	glTranslatef(-9.7, -3.0, 0);
	glColor4f(1.0, 1.0, 1.0, 0.5);
	glutSolidSphere(0.7, 20, 35);
	glPopMatrix();

	//power button inner
	glPushMatrix();
	glTranslatef(-9.7, -3.0, 0);
	glColor4f(0.5, 0.5, 0.5, 1.8);
	glutSolidSphere(0.6, 20, 35);
	glPopMatrix();
	//cpu button (reset) outer
	glPushMatrix();
	//glTranslatef(-9.7,-5.0,0);
	glColor4f(1.0, 1.5, 1.5, 0.5);
	glutSolidSphere(0.38, 20, 10);
	glPopMatrix();
	// Button inner(Reset)
	glPushMatrix();
	glTranslatef(-9.7, -5.0, 0);
	glColor4f(0.5, 0.5, 0.5, 1.2);
	glutSolidSphere(0.3, 20, 10);

	glPopMatrix();
	//CD rom
	glPushMatrix();
	glScalef(0.7, 0.2, 1);//it changes the place in  scale of the cd rom 
	glTranslatef(-14.0, 14.3, 0);
	glutSolidCube(5);
	glColor4f(1.0, 1.0, 1.0, 0.2);
	glutWireCube(5);//CD rom out line wire 
	glPopMatrix();
	//CD open key
	glPushMatrix();
	glScalef(0.3, 0.1, 1);
	glTranslatef(-28.0, 17.3, 0); //alter the current matrix by a displacement of (x,y,z)
	glutSolidCube(2); //display the cd open button cube of size 2
	glColor4f(1.5, 1.0, 3.5, 1.9);
	glPopMatrix();

	//These three PushMatrix is use for Usb ports
	glPushMatrix();
	glScalef(0.3, 0.15, 1);
	glTranslatef(-28.0, -65.3, 0);
	glColor4f(1.5, 1.5, 1.5, 0.8);
	glutSolidCube(2);//display the cube of the usb port of the cpu
	glPopMatrix();

	glPushMatrix();
	glScalef(0.3, 0.15, 1);
	glTranslatef(-33.0, -65.3, 0);
	glutSolidCube(2); //display the cube of the usb port of the cpu
	glColor4f(1.5, 1.5, 1.5, 0.8);
	glPopMatrix();

	glPushMatrix();
	glScalef(0.3, 0.15, 1);
	glTranslatef(-38.0, -65.3, 0);
	glutSolidCube(2);//display the cube of the usb port of the cpu 
	glColor4f(1.5, 1.5, 1.5, 0.8);
	glPopMatrix();


}

void connector()
{
	glPushMatrix();
	glRotatef(45, 1, 1, 0);
	glColor4f(0.3, 0.3, 0.3, con_blend);
	glutSolidCube(2);
	glColor4f(10, 10, 10, con_blend);
	glutWireCube(2.0);
	glPopMatrix();
}

void line()
{
	//////////////First pipe/////////////////////////
	glPushMatrix();
	glColor4f(0, 0, 0, 0.5);
	glTranslatef(-18.5, 10.5, 0);
	glRotatef(40, 1, 0, 0);
	Cylinder(cy_height_1);
	glPopMatrix();

	glPushMatrix();
	glColor4f(0, 0, 0, 0.5);
	glTranslatef(-18.5, 0.0, 0);
	glRotatef(180, 1, 0, 1);
	Cylinder(cy_height_1);
	glPopMatrix();

	////////////////2nd  Pipe//////////////////////
	glPushMatrix();
	glColor4f(0, 0, 0, 0.5);
	glTranslatef(18.7, 11.3, 0);
	glRotatef(45, 1, 0, 0);
	Cylinder(cy_height_4);
	glPopMatrix();

	glPushMatrix();
	glColor4f(0, 0, 0, 0.5);
	glTranslatef(18.9, 0.0, 0);
	glRotatef(-90, 0, 1, 0);
	Cylinder(cy_height_4);
	glPopMatrix();

	////////////////Third Pipe//////////////////////
	glPushMatrix();
	glColor4f(0, 0, 0, 0.5);
	glTranslatef(-18.7, -14.5, 0);
	glRotatef(15, 1, 0, 0);
	Cylinder(cy_height_2);
	glPopMatrix();

	glPushMatrix();
	glColor4f(0, 0, 0, 0.5);
	glTranslatef(-18.5, -20.5, 0);
	glRotatef(180, 1, 0, 1);
	Cylinder(cy_height_1);
	glPopMatrix();

	glPushMatrix();
	glColor4f(0, 0, 0, 0.5);
	glTranslatef(-0.8, -20.5, 0);
	glRotatef(-90, 1, 0, 0);
	Cylinder(cy_height_3_1);
	glPopMatrix();



	//Fourth Pipe	
	glPushMatrix();
	glColor4f(0, 0, 0, 0.5);
	glTranslatef(18.6, -15.0, 0);
	glRotatef(15, 1, 0, 0);
	Cylinder(cy_height_3);
	glPopMatrix();

	glPushMatrix();
	glColor4f(0, 0, 0, 0.5);
	glTranslatef(18.9, -20.7, 0);
	glRotatef(-90, 0, 1, 0);
	Cylinder(cy_height_4);
	glPopMatrix();

	glPushMatrix();
	glColor4f(0, 0, 0, 0.5);
	glTranslatef(0.8, -20.5, 0);
	glRotatef(-90, 1, 0, 0);
	Cylinder(cy_height_3_1);
	glPopMatrix();

}

void hub(float scr, float scg, float scb)
{

	glColor4f(1, 0.0, 0, 0.5);
	glPushMatrix();
	glScalef(1, 0.5, 0.5);
	glutSolidCube(6);
	glPopMatrix();

	glColor4f(0, 0.0, 0, 1);
	glPushMatrix();
	glTranslatef(-2.3, 0, 0);
	glutSolidCube(0.5);
	glTranslatef(1.5, 0, 0);
	glutSolidCube(0.5);
	glTranslatef(1.5, 0, 0);
	glutSolidCube(0.5);
	glTranslatef(1.5, 0, 0);
	glutSolidCube(0.5);
	glPopMatrix();

	glColor4f(0.2, 0.2, 0.2, 0.1);
	glPushMatrix();
	glScalef(0.9, 0.47, 0.5);
	glutSolidCube(7);
	glutWireCube(7);
	glPopMatrix();

	glColor4f(0.0, 0.0, 0.0, 0.25);
	glPushMatrix();
	glScalef(4.5, 0.5, 0);
	glutSolidTetrahedron();
	glPopMatrix();

	glColor4f(0.0, 0.0, 0.0, 0.2);
	glPushMatrix();
	glScalef(1.8, 0.23, 0);
	glTranslatef(0, 8.4, 0);
	glutSolidCube(3);
	glColor4f(0.7, 0.7, 0.7, 0.2);
	glutWireCube(3);
	glPopMatrix();


	glColor4f(scr, scg, scb, 1);
	glPushMatrix();
	glTranslatef(2.0, 1.95, 0);
	glColor4f(0.3, 1.2, 0.2, 0.6);
	glutSolidSphere(0.3, 20, 5);
	glPopMatrix();

	glFlush();
}
void anim()
{
	//Blinking effect of source computer
		//if(tr2<=12)
	if (blink_flag % 2 != 0)
	{
		if (c1b < 6)
			c1b += 0.5;
		if (c1b >= 6)
			c1b = 0;
	}
	if (tr2 > 12 || blink_flag % 2 == 0) {
		blink_flag = 2;
		c1r = -0.9; c1g = -0.9; c1b = 0.9; //Change color of source computer back to original color
	}
	if (cy_flag == 1)
	{
		if (tr <= 12)
			tr += 0.07;
		if (tr > 12 && tr1 <= 37.3)
			tr1 += 0.07;
		if (tr1 > 37.2 && tr2 <= 12)
		{
			flag = 1;
			tr2 += 0.07;
		}


		if (tr2 > 12)//Blinking effect of 2nd computer
		{
			if (c2b < 5)
				c2b += 0.5;
			else if (c2b >= 5)
				c2b = 0;
			blink_flag = 2;
		}
	}

	//data flow b/w 1st computer to 3rd computer
	if (cy_flag1 == 1)
	{
		if (tr3 <= 12)
			tr3 += 0.07;
		if (tr3 > 12 && tr4 <= 17.75)
			tr4 += 0.07;
		if (tr4 > 17.75 && tr5 <= 20.3)
		{
			flag = 1;
			tr5 += 0.07;
		}
		if (tr5 > 20.3 && tr6 <= 17.9)
		{
			flag1 = 1;
			tr6 += 0.07;
		}
		if (tr6 > 17.8 && tr7 <= 5.5)
		{
			flag2 = 1;
			tr7 += 0.07;
		}

		//Blinking effect of source computer
			//if(tr6<=17.8)
			//{
			//	if(c1b<6)
			//		c1b+=0.5;
			//	if(c1b>=6)
			//		c1b=0;
			//}
			//else {
			//	c1r=-0.9;c1g=-0.9;c1b=0.9; //Change color of source computer back to original color
			//}
		if (tr6 > 17.8)//Blinking effect of 3rd computer
		{
			if (c3b < 6)
				c3b += 0.5;
			if (c3b >= 6)
				c3b = 0;
			if (tr6 < 17.9)
				blink_flag = 2;
		}

	}

	//data movement 4m 1st to 4th
	if (cy_flag2 == 1)
	{
		if (tr8 <= 12)
			tr8 += 0.07;
		if (tr8 > 12 && tr9 <= 19.5)
			tr9 += 0.07;
		if (tr9 > 19.5 && tr10 <= 20.3)
		{
			flag3 = 1;
			tr10 += 0.07;
		}
		if (tr10 > 20.3 && tr11 <= 17.9)
		{
			flag4 = 1;
			tr11 += 0.07;
		}
		if (tr11 > 17.8 && tr12 <= 5.5)
		{
			flag5 = 1;
			tr12 += 0.07;
			if (tr11 < 17.9)
				blink_flag = 2;
		}

		////Blinking effect of source computer
		//	if(tr6<=17.8)
		//	{
		//		if(c1b<6)
		//			c1b+=0.5;
		//		if(c1b>=6)
		//			c1b=0;
		//	}
		//	else {
		//		c1r=-0.9;c1g=-0.9;c1b=0.9; //Change color of source computer back to original color
		//	}
		if (tr6 > 17.8)//Blinking effect of destination computer
		{
			if (c3b < 6)
				c3b += 0.5;
			if (c3b >= 6)
				c2b = 0;
		}
	}

	if (cy_height_1 <= 16.5)
		cy_height_1 += 0.1;
	if (cy_height_2 <= 20.0)
		cy_height_2 += 0.1;
	if (cy_height_3 <= 20)
		cy_height_3 += 0.1;
	if (cy_height_3_1 <= 21)
		cy_height_3_1 += 0.1;
	//if(cy_height_3_1>21)
	//	//cy_flag=1;
	if (cy_height_4 <= 17)
		cy_height_4 += 0.1;


	glutPostRedisplay();
}
void animate(int value)
{
	if (hub1 == 1)
	{
		if (dis <= 27.0)
			dis += 0.2;

		else if (con_blend <= 1.0)
			con_blend += 0.01;
	}
	glutPostRedisplay();
	glutTimerFunc(30, animate, 0);
}
void text1(float a, float b,const char* ptr, float r1, float g1, float b1)
{
	int len1 = strlen(ptr);
	glColor3f(r1, g1, b1);
	glRasterPos2d(a, b);
	for (int i = 0; i < len1; i++)
		glutBitmapCharacter(GLUT_BITMAP_HELVETICA_10, ptr[i]);
}
void text3(float a, float b,const char* ptr)
{
	int len1 = strlen(ptr);
	glColor3f(8.9, 2.0, 1.5);
	glRasterPos2d(a, b);
	for (int i = 0; i < len1; i++)
		glutBitmapCharacter(GLUT_BITMAP_HELVETICA_12, ptr[i]);
}
void text4(float a, float b,const char* ptr)
{
	int len1 = strlen(ptr);
	glColor3f(4.9, 2.0, 5.5);
	glRasterPos2d(a, b);
	for (int i = 0; i < len1; i++)
		glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24, ptr[i]);
}

void text2(float a, float b,const char* ptr, float red, float green, float blue)
{
	int len1 = strlen(ptr);
	glColor3f(red, green, blue);
	glRasterPos2d(a, b);
	for (int i = 0; i < len1; i++)
		glutBitmapCharacter(GLUT_BITMAP_HELVETICA_18, ptr[i]);
}

void demo_menu(int id)
{
	switch (id)
	{
	case 1:
		break;
	case 4: connec = 1;
		break;
	case 5: hub1 = 1;
		break;
	}
	glutPostRedisplay();
}

void option_menu(int id)
{
	switch (id)
	{
	case 1:
		break;
	}
	glutPostRedisplay();
}

void computer1(int id)
{
	switch (id)
	{
	case 1:cy_flag = 1;
		blink_flag = 1;
		break;
	case 2:cy_flag1 = 1;
		blink_flag = 3;
		break;
	case 3:cy_flag2 = 1;
		blink_flag = 5;
		break;
	}
	glutPostRedisplay();
}



void mymouse(int btn, int state, int x, int y)
{
	if (btn == GLUT_LEFT_BUTTON && state == GLUT_DOWN)
	{
		//glutIdleFunc(anim);
	}
	if (btn == GLUT_RIGHT_BUTTON && state == GLUT_DOWN)
	{

	}
	if (btn == GLUT_MIDDLE_BUTTON && state == GLUT_DOWN)
	{
		exit(0);
	}
}
void packet1()
{

	glPushMatrix();
	glTranslatef(-15.6, 19, 0);
	glColor4f(0.9, 1.5, 0, 1);
	glutSolidSphere(0.4, 10, 10);
	glPopMatrix();
}
void packet2()
{

	glPushMatrix();
	glTranslatef(-15.6, 19, 0);
	glColor4f(0.9, 1.5, 0, 1);
	glutSolidSphere(0.4, 10, 10);
	glPopMatrix();
}
void packet3()
{

	glPushMatrix();
	glTranslatef(-15.6, 19, 0);
	glColor4f(0.9, 1.5, 0, 1);
	glutSolidSphere(0.4, 10, 10);
	glPopMatrix();
}
void display(void)
{
	glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

	GLfloat amb[] = { 0.4,0.3,0.3,0.5 };
	GLfloat diff[] = { 1.0,1.0,0.5,0.5 };
	GLfloat spec[] = { 1.0,1.0,1.0,0.5 };
	GLfloat shi[] = { 50.0 };
	glMaterialfv(GL_FRONT, GL_AMBIENT, amb);
	glMaterialfv(GL_FRONT, GL_DIFFUSE, diff);
	glMaterialfv(GL_FRONT, GL_SPECULAR, spec);
	glMaterialfv(GL_FRONT, GL_SHININESS, shi);

	GLfloat lightintensity[] = { 1.0, 1.0, 1.0, 1.0 };
	GLfloat lightposition[] = { 50.0, 25.0, 15.7, 0.0 };
	glLightfv(GL_LIGHT0, GL_POSITION, lightposition);
	glLightfv(GL_LIGHT0, GL_DIFFUSE, lightintensity);

	glEnable(GL_LIGHTING);
	glEnable(GL_LIGHT0);
	glEnable(GL_COLOR_MATERIAL);
	glShadeModel(GL_SMOOTH);
	//glEnable(GL_DEPTH_TEST);
	glEnable(GL_NORMALIZE);

	// 1st computer
	glPushMatrix();
	glPushMatrix();
	glScalef(0.6, 0.6, 0.6);
	glTranslatef(-21, 28, 0);
	//glRotatef(-20, 0.0, 1.0, 0.0);
	cpu();
	glPopMatrix();
	glScalef(0.6, 0.6, 0.6);
	glRotatef(30, 1, 1, 0.0);
	glTranslatef(-23, 30, 0);
	computer(c1r, c1g, c1b);		//these parameters show blinking effect and back to normal position. 

	glPopMatrix();


	//2nd Computer	
	glPushMatrix();
	glPushMatrix();
	glScalef(0.6, 0.6, 0.6);
	glTranslatef(41, 28, 0);
	//glRotatef(20, 0, 0.1, 0.0);
	cpu();
	glPopMatrix();
	glScalef(0.6, 0.6, 0.6);
	glRotatef(30, 1.0, 1.0, 0.0);
	glTranslatef(20, 28, 0);
	computer(c2r, c2g, c2b);

	glPopMatrix();

	//3rd computer
	glPushMatrix();
	glPushMatrix();
	glScalef(0.6, 0.6, 0.6);
	glTranslatef(-21, -17, 0);
	//glRotatef(20, 0, 0.1, 0.0);
	cpu();
	glPopMatrix();
	glScalef(0.6, 0.6, 0.6);
	glRotatef(30, 1.0, 1.0, 0.0);
	glTranslatef(-19, -17, 0);
	computer(c3r, c3g, c3b);

	glPopMatrix();

	//4th Computer
	glPushMatrix();
	glPushMatrix();
	glScalef(0.6, 0.6, 0.6);
	glTranslatef(41, -16, 0);
	//glRotatef(30, 1, 0, 1);
	cpu();
	glPopMatrix();
	glScalef(0.6, 0.6, 0.6);
	glRotatef(30, 1.0, 1.0, 0.0);
	glTranslatef(22, -19, 0);
	computer(c4r, c4g, c4b);

	glPopMatrix();
	if (dis < 27)
	{
		text1(-13.9, 17.5, "I WANT TO SHARE ", 5, 5, 5);
		text1(-13.9, 16.5, "SOME DATA WITH MY", 5, 5, 5);
		text1(-13.9, 15.5, " NEIGHBOUR.", 5, 5, 5);
		text1(-13.9, 14.5, " BUT HOW??", 5, 5, 5);
	}
	else if (tr < 11)
		text1(4, 1, "HEY DONT PANIC, IM HERE TO ASSIST YOU.", -5, -5, -5);
	else if (tr2 < 12)
		text2(-12.8, 15.5, "Hello", 0.8, 1, 0);
	else if (tr2 > 12)
		text2(11.8, 15.9, "Hello", 0.8, 1, 0);
	//Hub Movement to the centre
	glPushMatrix();
	glTranslatef(-27 + dis, 0, 0);
	hub(Hub_R, Hub_G, 0);
	glPopMatrix();
	if (dis > 20)
	{
		if (connec == 1)
		{
			line();
			glutIdleFunc(anim);
		}
		glPushMatrix();
		glTranslatef(-18.5, 0, 0);
		connector();
		glPopMatrix();

		glPushMatrix();
		glTranslatef(18.5, 0, 0);
		connector();
		glPopMatrix();

		glPushMatrix();
		glTranslatef(-18.7, -20.5, 0);
		connector();
		glPopMatrix();

		glPushMatrix();
		glTranslatef(18.7, -20.5, 0);
		connector();
		glPopMatrix();

		glPushMatrix();
		glTranslatef(0, -20.5, 0);
		glScalef(2, 1, 1);
		connector();
		glPopMatrix();

		glPushMatrix();
		if (tr <= 12)
			glTranslatef(-3, -7 - tr, 1);
		else if (tr > 12)
			glTranslatef(-3 + tr1, -7 - tr, 1);
		if (flag == 1)
			glTranslatef(0, tr2, 0);
		packet1();
		glPopMatrix();

		glPushMatrix();
		if (tr3 <= 12)
			glTranslatef(-3, -7 - tr3, 1);
		else if (tr3 > 12)
			glTranslatef(-3 + tr4, -7 - tr3, 1);
		if (flag == 1)
			glTranslatef(0, 0 - tr5, 0);
		if (flag1 == 1)
			glTranslatef(0 - tr6, 0, 0);
		if (flag2 == 1)
			glTranslatef(0, 0 + tr7, 0);
		packet2();
		glPopMatrix();

		//data movement from 1st to 4th
		glPushMatrix();
		if (tr8 <= 12)
			glTranslatef(-3, -7 - tr8, 1);
		else if (tr8 > 12)
			glTranslatef(-3 + tr9, -7 - tr8, 1);
		if (flag3 == 1)
			glTranslatef(0, 0 - tr10, 0);
		if (flag4 == 1)
			glTranslatef(0 + tr11, 0, 0);
		if (flag5 == 1)
			glTranslatef(0, 0 + tr12, 0);
		packet3();
		glPopMatrix();

	}
	text3(-19.4, 16, "DELL");
	text3(17.9, 16.2, "DELL");
	text3(-19.4, -10.5, "DELL");
	text3(17.9, -10, "DELL");
	text4(-4, 20, "STAR TOPOLOGY");


	glutSwapBuffers();
	glFlush();
}

void mypoint()
{
	glClearColor(0.5, 0.9, 0.7, 0.5);
	glOrtho(-23.0, 23.0, -23.0, 23.0, -43.0, 43.0);
	glEnable(GL_BLEND);
	glBlendFunc(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);
}

int main(int argc, char* argv)
{
	glutInit(&argc, &argv);
	glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB);
	glutInitWindowSize(500, 500);
	glutCreateWindow("STAR TOPOLOGY");
	mypoint();
	glutDisplayFunc(display);

	int	sub_menu_1 = glutCreateMenu(computer1);
	glutAddMenuEntry("To computer 2", 1);
	glutAddMenuEntry("To computer 3", 2);
	glutAddMenuEntry("To computer 4", 3);

	int	sub_menu = glutCreateMenu(option_menu);
	glutAddSubMenu("From computer 1", sub_menu_1);


	/*glutAddMenuEntry("From computer 2",2);
	glutAddMenuEntry("From computer 3",3);
	glutAddMenuEntry("From computer 4",4);*/

	glutCreateMenu(demo_menu);
	glutAddMenuEntry("HUB", 5);
	glutAddMenuEntry("CONNECTION", 4);
	glutAddSubMenu("SEND MESSAGE", sub_menu);
	//glutAddSubMenu("HUB FAIL",5);

	glutAttachMenu(GLUT_RIGHT_BUTTON);
	glutMouseFunc(mymouse);
	anim();
	animate(0);
	//glutFullScreen();
	glutMainLoop();
	return(0);
}
