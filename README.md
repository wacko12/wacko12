#include <iostream.h>
#include <stdlib.h>

class X
{
    protected:
        int *x1, *x2; 

    public:

        X(int a, int b)
        {
            x1 = new int;
            x2 = new int;
            *x1 = a;
            *x2 = b;
        }

        virtual void view()
        {
            cout << "x1=" << *x1 << " x2=" << *x2 << endl;
        }

        virtual void set_new()
        {
            cout << "Input x1: ";
            cin >> *x1;
            cout << "Input x2: ";
            cin >> *x2;
        }

        ~X()
        {
            delete x1;
            delete x2;
        }
};

class Y:public X
{
    private:
        int *y; 

    public:

        Y(int a, int b, int c):X(a,b)
        {
            y = new int;
            *y = c;
        }

        virtual void view()
        {
            cout << "x1=" << *x1 << " x2=" << *x2 << " y=" << *y << endl;
        }

        virtual void set_new()
        {
            cout << "Input x1: ";
            cin >> *x1;
            cout << "Input x2: ";
            cin >> *x2;
            cout << "Input y: ";
            cin >> *y;
        }

        ~Y()
        {
            delete y;
        }

        void Run()
        {
            cout << "Res: " << ( *x1 * *x2 ) + *y << endl;
        }
};

void main()
{
    X *t; 
    t = new X(10,20); 
    t->view(); 
    t->set_new(); 
    t->view(); 

    delete t; 

    t = new Y(100, 50, 2); 
    t->view();
    t->set_new();
    t->view(); 


    ((Y*) t)->Run();   

    delete t; 
}
