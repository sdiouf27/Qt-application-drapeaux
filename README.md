# Qt-application-drapeaux
mainwindow.h
#ifndef MAINWINDOW_H
#define MAINWINDOW_H
#include <Color.h>
#include <Drapeau.h>
#include <QPushButton>
#include <QHBoxLayout>
#include <QStackedLayout>
#include <QLabel>
#include <QMainWindow>

QT_BEGIN_NAMESPACE
namespace Ui { class MainWindow; }
QT_END_NAMESPACE

class MainWindow : public QMainWindow
{
	Q_OBJECT

public:
	MainWindow(QWidget *parent = nullptr);
	~MainWindow();
	//--- Déclaration des boutons ---//
	QPushButton *B1 = new QPushButton("ALLEMAGNE");
	QPushButton *B2 = new QPushButton("FRANCE");
	QPushButton *B3 = new QPushButton("AUTRICHE");
	QPushButton *B4 = new QPushButton("BELGIQUE");
	QPushButton *B5 = new QPushButton("ESTONIE");
	QPushButton *B6 = new QPushButton("HONGRIE");
	QPushButton *B7 = new QPushButton("IRLANDE");
	QPushButton *B8 = new QPushButton("ITALIE");
	QPushButton *B9 = new QPushButton("LETTONIE");
	QPushButton *B10 = new QPushButton("LUTIANIE");
	QPushButton *B11 = new QPushButton("LUXEMBOURG");
	QPushButton *B12 = new QPushButton("PAYS BAS");
	QPushButton *B13 = new QPushButton("ROUMANIE");

public slots:
	void Drapeau_ALLEMAGNE(); // Déclaration du slot
	void Drapeau_FRANCE();	// Déclaration d'un autre slot (exemple)
	void Drapeau_AUTRICHE();	// Déclaration d'un autre slot (exemple)
	void Drapeau_BELGIQUE();	// Déclaration d'un autre slot (exemple)
	void Drapeau_ESTONIE();	// Déclaration d'un autre slot (exemple)
	void Drapeau_HONGRIE();	// Déclaration d'un autre slot (exemple)
	void Drapeau_IRLANDE();	// Déclaration d'un autre slot (exemple)
	void Drapeau_ITALIE();	// Déclaration d'un autre slot (exemple)
	void Drapeau_LETTONIE();	// Déclaration d'un autre slot (exemple)
	void Drapeau_LUTIANIE();	// Déclaration d'un autre slot (exemple)
	void Drapeau_LUXEMBOURG();	// Déclaration d'un autre slot (exemple)
	void Drapeau_PAYS_BAS();	// Déclaration d'un autre slot (exemple)
	void Drapeau_ROUMANIE();	// Déclaration d'un autre slot (exemple)

private:
	Ui::MainWindow *ui;
};

mainwindow.cpp
#endif // MAINWINDOW_H
mainwindow.cpp 
#include "mainwindow.h"
#include "ui_mainwindow.h"
#include <QMessageBox>
#include <QPixmap>
#include <QHBoxLayout>
#include <QVBoxLayout>
#include <QPushButton>
#include "Drapeau.h"

//Constructeur de MainWindow
MainWindow::MainWindow(QWidget *parent)
	: QMainWindow(parent)
	, ui(new Ui::MainWindow)
{
	ui->setupUi(this);
	setWindowTitle("Drapeaux tricolores UE");
	resize(700, 400);

	QPixmap bkgnd("/home/ciel2024/diouf_drapeaux/build/drapeau-europe.jpeg");
	bkgnd = bkgnd.scaled(this->size(), Qt::IgnoreAspectRatio);
	QPalette palette;
	palette.setBrush(QPalette::Background, bkgnd);
	this->setPalette(palette);

	//--- Layout des boutons ---//
	QVBoxLayout *Pagelayout = new QVBoxLayout;
	QHBoxLayout *Hlayout1 = new QHBoxLayout;
	QHBoxLayout *Hlayout2 = new QHBoxLayout;

	// Ajoutez les layouts au layout principal
	Pagelayout->addLayout(Hlayout1);
	Pagelayout->addLayout(Hlayout2);

	// Créez et dimensionnez les boutons
	this->B1->setGeometry(50, 100, 100, 50);
	this->B2->setGeometry(50, 100, 100, 50);
	this->B3->setGeometry(50, 100, 100, 50);
	this->B4->setGeometry(50, 100, 100, 50);
	this->B5->setGeometry(50, 100, 100, 50);
	this->B6->setGeometry(50, 100, 100, 50);
	this->B7->setGeometry(50, 100, 100, 50);
	this->B8->setGeometry(50, 100, 100, 50);
	this->B9->setGeometry(50, 100, 100, 50);
	this->B10->setGeometry(50, 100, 100, 50);
	this->B11->setGeometry(50, 100, 100, 50);
	this->B12->setGeometry(50, 100, 100, 50);
	this->B13->setGeometry(50, 100, 100, 50);

	//--- Connexion des signaux aux slots ---//
	connect(B1, SIGNAL(clicked()), this, SLOT(Drapeau_ALLEMAGNE()));
	connect(B2, SIGNAL(clicked()), this, SLOT(Drapeau_FRANCE()));
	connect(B3, SIGNAL(clicked()), this, SLOT(Drapeau_AUTRICHE()));
	connect(B4, SIGNAL(clicked()), this, SLOT(Drapeau_BELGIQUE()));
	connect(B5, SIGNAL(clicked()), this, SLOT(Drapeau_ESTONIE()));
	connect(B6, SIGNAL(clicked()), this, SLOT(Drapeau_HONGRIE()));
	connect(B7, SIGNAL(clicked()), this, SLOT(Drapeau_IRLANDE()));
	connect(B8, SIGNAL(clicked()), this, SLOT(Drapeau_ITALIE()));
	connect(B9, SIGNAL(clicked()), this, SLOT(Drapeau_LETTONIE()));
	connect(B10, SIGNAL(clicked()), this, SLOT(Drapeau_LUTIANIE()));
	connect(B11, SIGNAL(clicked()), this, SLOT(Drapeau_LUXEMBOURG()));
	connect(B12, SIGNAL(clicked()), this, SLOT(Drapeau_PAYS_BAS()));
	connect(B13, SIGNAL(clicked()), this, SLOT(Drapeau_ROUMANIE()));

	//--- Ajout des boutons aux layouts ---//
	Hlayout1->addWidget(B1);
	Hlayout1->addWidget(B2);
	Hlayout1->addWidget(B3);
	Hlayout1->addWidget(B4);
	Hlayout1->addWidget(B5);
	Hlayout1->addWidget(B6);
	Hlayout2->addWidget(B7);
	Hlayout2->addWidget(B8);
	Hlayout2->addWidget(B9);
	Hlayout2->addWidget(B10);
	Hlayout2->addWidget(B11);
	Hlayout2->addWidget(B12);
	Hlayout2->addWidget(B13);


	QWidget *widget = new QWidget;
	widget->setLayout(Pagelayout);
	setCentralWidget(widget);
}


//--- Slot pour le drapeau d'Allemagne ---//
void MainWindow::Drapeau_ALLEMAGNE() {
	Drapeau *D = new Drapeau("black", "red", "yellow", "vertical", "Allemagne");

}
//--- Slot pour le drapeau de France ---//
void MainWindow::Drapeau_FRANCE() {
	Drapeau *D = new Drapeau("blue", "white", "red", "horizontal", "France");

}
void MainWindow::Drapeau_AUTRICHE() {
	Drapeau *D = new Drapeau("red", "white", "red", "vertical", "Autriche");

}
void MainWindow::Drapeau_BELGIQUE() {
	Drapeau *D = new Drapeau("Black", "yellow", "red", "horizontal", "Begique");

}
void MainWindow::Drapeau_ESTONIE() {
	Drapeau *D = new Drapeau("blue", "black", "white", "vertical", "Estonie");

}
void MainWindow::Drapeau_HONGRIE() {
	Drapeau *D = new Drapeau("red", "white", "green", "vertical", "Hongrie");

}
void MainWindow::Drapeau_IRLANDE() {
	Drapeau *D = new Drapeau("green", "white", "orange", "horizontal", "Irlande");

}
void MainWindow::Drapeau_ITALIE() {
	Drapeau *D = new Drapeau("Green", "white", "red", "horizontal", "Italie");

}
void MainWindow::Drapeau_LETTONIE() {
	Drapeau *D = new Drapeau("red", "white", "red", "vertical", "Lettonie");

}
void MainWindow::Drapeau_LUTIANIE() {
	Drapeau *D = new Drapeau("gold", "green", "red", "vertical", "Lutianie");

}
void MainWindow::Drapeau_LUXEMBOURG() {
	Drapeau *D = new Drapeau("red", "white", "skyblue", "vertical", "Luxembourg");

}
void MainWindow::Drapeau_PAYS_BAS() {
	Drapeau *D = new Drapeau("red", "white", "darkblue", "vertical", "Pays bas");

}
void MainWindow::Drapeau_ROUMANIE() {
	Drapeau *D = new Drapeau("blue", "gold", "red", "horizontal", "Roumanie");

}

//--- Destructeur ---//
MainWindow::~MainWindow() {
	delete ui;
}
color.cpp
#include "Color.h"
#include <QPalette>
#include <QString>
#include <QColor>

//--- Constructeur par défaut ---//
Color::Color(QWidget *parent)
	: QWidget(parent) {
	setGeometry(0, 0, 100, 100);
	this->setAutoFillBackground(true); // # couleur d'arrière-plan
}

//--- Constructeur qui prend une couleur comme paramètre ---//
Color::Color(QString couleur)
{ // Assurez-vous d'utiliser QWidget(parent) si vous le souhaitez
	setGeometry(0, 0, 100, 100);
	this->setAutoFillBackground(true); // # couleur d'arrière-plan
	QPalette maPalette = palette(); // # définir une palette
	// On ajoute la couleur passée en paramètre
	maPalette.setColor(QPalette::Window, QColor(couleur));
	setPalette(maPalette); // # Palette ajoutée au widget
}

//--- Destructeur ---//
Color::~Color() {
}

color.h
#ifndef COLOR_H
#define COLOR_H
#include <QWidget>
#include <QHBoxLayout>
#include <QVBoxLayout>

	QT_BEGIN_NAMESPACE
	namespace Ui { class Widget; }
	QT_END_NAMESPACE

	class Color : public QWidget
	{
    	Q_OBJECT

	public:
    	Color(QWidget *parent = nullptr);
    	Color(QString couleur);
    	~Color();

	private:
    	//Ui::Widget *ui;
	};
#endif // COLOR_H

Drapeau.h
#ifndef DRAPEAU_H
#define DRAPEAU_H
#include <QWidget>
#include <QHBoxLayout>
#include <QVBoxLayout>
	class Drapeau : public QWidget
                  	{
	Q_OBJECT

    	public:
        	Drapeau(QWidget *parent = nullptr);
	Drapeau(QString C1, QString C2, QString C3, QString type,
        	QString title);
	~Drapeau();
	QHBoxLayout *Horiz_layout = new QHBoxLayout;
	QVBoxLayout *Vertic_layout = new QVBoxLayout;


    	private:
    	//Ui::Widget *ui;
        	};
#endif // DRAPEAU_H

Drapeau.cpp
#include "Drapeau.h"
#include "Color.h"

//--- Classe Drapeau ---//
Drapeau::Drapeau(QWidget *parent)
	: QWidget(parent) {

}

Drapeau::Drapeau(QString C1, QString C2, QString C3, QString type, QString title)
{

	//--- Objets de la classe Color ---//
	Color *Couleur1 = new Color(C1);
	Color *Couleur2 = new Color(C2);
	Color *Couleur3 = new Color(C3);

	if (type == "horizontal") { // Exemple de drapeau horizontal
    	Horiz_layout->addWidget(Couleur1);
    	Horiz_layout->addWidget(Couleur2);
    	Horiz_layout->addWidget(Couleur3);
    	Horiz_layout->setSpacing(0);
    	Horiz_layout->setMargin(0); // Utilisez setContentsMargins au lieu de setMargin

    	QWidget *widget = new QWidget;
    	widget->setLayout(Horiz_layout);
    	widget->resize(400, 400);
    	widget->setWindowTitle(title); // Utiliser le titre du pays
    	widget->show();
	} else if (type == "vertical") { // Exemple de drapeau vertical
    	Vertic_layout->addWidget(Couleur1);
    	Vertic_layout->addWidget(Couleur2);
    	Vertic_layout->addWidget(Couleur3);
    	Vertic_layout->setSpacing(0);
    	Vertic_layout->setMargin(0);

    	QWidget *widget = new QWidget;
    	widget->setLayout(Vertic_layout);
    	widget->resize(400, 400);
    	widget->setWindowTitle(title); // Utiliser le titre du pays
    	widget->show();
	}
}

Drapeau::~Drapeau() {

}

main.cpp
#include "mainwindow.h"

#include <QApplication>

int main(int argc, char *argv[])
{
	QApplication a(argc, argv);
	MainWindow w;
	w.show();
	return a.exec();
}









