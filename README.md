# Tarea-04
##*Tarea 04 de la unidad 4 de POO*
## 1. Considera el siguiente fragmento de programa:

```csharp
using System;
using System.Collections.Generic;
using System.Text;


namespace tarea41
{
  class A

    {

    public int a;

    public A()

        {

        a = 10;

        }

     public virtual string Display()

      {

      return a.ToString();

      }

    }
 


class B:A

   {

   public int b;

   public B():base()

   {
     

    b = 15;

   }
 

  //  #  Después de contestar la pregunta 1                  

 //   #  Redefine el método Display( ) en este espacio,  debe regresar el campo b como string.
     
   public override string Display()

      {

      return b.ToString();

      }
  
}

 class Program

  {

   public static void Main()

   {

  A objA = new A();

  B objB = new B();

  Console.WriteLine(objA.Display()); ////  (1 )

  Console. WriteLine(objB.Display()); ////  ( 2)


  }
}
}




```



**1.1. ¿Qué valores imprimen las lineas (1) y (2) ?**
10 
10

**1.2.  Redefine el método Display en el espacio indicado, una vez redefinido el método, ¿qué valores imprimen las lineas (1) y (2) ?.**
10
15

**1.3. ¿Que palabra debes agregar en la linea (public _______ string Display()) al definir A.Display()?**

Virtual

``` csharp 
 class A

    {

    public int a;

    public A()

        {

        a = 10;

        }

     public virtual string Display()

      {

      return a.ToString();

      }
```

## 2. Considera el siguiente fragmento de programa:
```csharp
using System;

using System.Collections.Generic;

 ________ class Musico

    {

    public string nombre;

    public Musico (string n)

        {

         nombre = n;

        }

   public abstract (A) void Afina();  (B)

   public (C) string Display()

      { 

       return nombre;

      }

   }

class Bajista; Musico

  {

    public string instrumento;

    public Bajista (string n, string i ) ......

    .........

    public _________ Afina()

      {

      ________________

      }

 }

class Guitarrista ____________

     {

     public instrumento;

      // Falta el constructor y otras cosas??

 

     }

 

class Program

 {

  public static Main()

   {

  Musico m = new Musico("Django"); (D)

  Bajista b = new Bajista("Flea");

  Guitarrista g = new Guitarrista("Santana");

  Musico [] m = ____________________

  m[0] = b;

  m[1] = g;

 

  foreach ( ___________)

       _____________________

 

 Console.ReadKey();

  

 }

}
```
**2.1. Completa el programa.**

```csharp

using System;
using System.Collections.Generic;

namespace tarea42
{
abstract class Musico

    {

    public string nombre;

    public Musico (string n)
        {
         nombre = n;
        }

   public abstract string  Afina(); //A y B
   public abstract string  Saluda();   
   
   public string Display()   //C

      { 

       return nombre;

      }
   }

class Bajista: Musico
  {
    public string bajo;
        public Bajista (string n, string bajo ):base(n)
    {
        this.bajo=bajo;
    }

    public override string Saluda()
      {
          return String.Format("Hola, mi nombre es {0}",nombre);

      }
      public override string Afina()
     {
         return "afino mi bajo";
     }
      
 }

class Guitarrista: Musico
     {

     public string guitarra;

      // Falta el constructor y otras cosas??
     public Guitarrista(string nombre, string guitarra): base(nombre)
     {
         this.guitarra=guitarra;
     }
     public override string Saluda()
      {
          return String.Format("Hola, mi nombre es {0}",nombre);

      }
     public override string Afina()
     {
         return "afino mi guitarra";
     }
 }
 class Vocalista: Musico
     {

     public string voz;
     public Vocalista(string nombre, string voz): base(nombre)
     {
         this.voz=voz;
     }

     public override string Saluda()
      {
          return String.Format("Hola, mi nombre es {0}",nombre);

      }
     public override string Afina()
     {
         return "afino mi voz";
     }
  }
  class Pianista: Musico
     {

     public string piano;
     public Pianista(string nombre, string piano): base(nombre)
     {
         this.piano=piano;
     }
     public override string Saluda()
      {
          return String.Format("Hola, mi nombre es {0}",nombre);

      }
     public override string Afina()
     {
         return "afino mi piano";
     }
  }
class Program
 {
    static void Main()
   {
      
    // m = new Musico(); //(D)
   

    Bajista b = new Bajista("Flea","bajo");
    Guitarrista g = new Guitarrista("Santana","guitarra");
    Vocalista v=new Vocalista("Sia","voz");
    Pianista p=new Pianista("Alexandra","piano");
     List<Musico>musicos=new List<Musico>();
    musicos.Add(b);
    musicos.Add(g);
    musicos.Add(v);
    musicos.Add(p);
  

  foreach (Musico mu in musicos)
  {
      Console.WriteLine(mu.Saluda());
      Console.WriteLine(mu.Afina());
      
  }
}
}
}
```

**2.2. Hay un error en uno de los puntos (A)(B)(C)(D). ¿Cuál es y por qué?**
- En el punto **A** no lleva void, ya que este es módulo de código que se ejecuta cuando es llamado desde algún punto del programa y no devuelve un valor.
- El punto **D** marca error porque no se puede crear una clase o interfaz abstracta.

**2.3. ¿Qué método se debe implementar obligatoriamente en ambas clases y por qué?**
 Primero que nada los métodos son todos aquellos bloques de código que se ocupan de manejar los datos de la clase.
 En este caso el método Afina es el que es indispensable para ambas clases.

**2.4. ¿Por qué no se ponen las llaves en (B)?, ¿Cuando si se pondrían?**
Porque es un método abstracto y cuando se declara "abstrac" no lleva un cuerpo definido así que simplemente se agrega ";"

**2.5. ¿Qué pasa si el método Afina() lo hacemos virtual en lugar de abstract?**
Tendiamos que desarrollar el cuerpo del método.

**3. Implementa el programa utilizando interfaces en lugar de herencia.**

````csharp

using System;
using System.Collections.Generic;

namespace tarea42
{
    interface IMusico
    {
        void Afina();
        
    }
 

class Bajista: IMusico
  {
      public void Afina()
      {
          Console.WriteLine("Estoy afinando mi bajo");
      }
  }

class Guitarrista: IMusico
     {
         public void Afina()
         {
             Console.WriteLine("Estoy afinando mi guitarra");
         }

     }
     class Pianista: IMusico
     {
         public void Afina()
         {
             Console.WriteLine("Estoy afinando mi piano");
         }

     }

  
class Program
 {
    static void Main()
   {
      Dictionary<String,IMusico>dict=new Dictionary<String,IMusico>();

      dict.Add("Fender Deluxe",new Bajista());
      dict.Add("Gibson",new Guitarrista());
      dict.Add("Yamaha", new Pianista());

      IMusico musicos;

      foreach(String key in dict.Keys)
      {
          if (dict.TryGetValue(key,out musicos))
          musicos.Afina();
          else

          Console.WriteLine("No estan afinando ");

      }
   
    }
}
}


```

