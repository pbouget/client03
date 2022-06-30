# 7 - @OneToOne (corrigé): ASSOCIATION BIDIRECTIONNELLE DE 1 VERS 1 (**client03**)

TRAVAIL A REALISER :

- mettre en place une **association bidirectionnelle** de **@OneToOne** entre Client et Adresse. Cela signifie que l’on pourra accéder à l’Adresse depuis Client et au Client depuis l’Adresse. Il y aura donc un attribut de chaque type dans chacune des entités.

- Créer le projet **client03**
- reprendre le code du projet **client02**
- modifier la classe **Adresse**
- le repository pour l'adresse n'est pas obligatoire !

La classe entité **Adresse** comportera un attribut supplémentaire : *client* de type **Client**.

```java
    private int id;
    private String voie;
    private String complement;
    private String codePostal;
    private String ville;
    private String pays;
    private Client client;
```

## Mise en place de l’association bidirectionnelle de un vers un

La navigabilité de l’association est de Client vers Adresse et de Adresse vers Client.

L’annotation **@OneToOne** sur la méthode **getAdresse()** de Client indique la navigabilité de Client vers Adresse.

```java
    @OneToOne(cascade={CascadeType.ALL})
    @JoinColumn(name="ADDRESS_ID")
    public Adresse getAdresse() {
        return adresse;
    }
```

L’annotation **@OneToOne** sur la méthode **getClient()** de Adresse indique la navigabilité de Adresse vers Client.

>La propriété « **mappedBy** » indique que le propriétaire ou le maître de la relation est déterminée du côté Client. **L’attribut qui est associé à la propriété mappedBy est ici le nom de l’attribut de type Adresse**, soit « adresse » en minuscule qui se trouve dans Client.

```java
    @OneToOne(mappedBy="adresse")
    public Client getClient() {
        return client;
    }
```

- Lancez l'application Spring Boot et observez les tables générées dans votre base de données.

- Appelez la méthode **home()** dans votre navigateur pour initialiser les clients en base de données en saisissant l'url ci-dessous dans votre navigateur :
  
[http://localhost:8080/accueil](http://localhost:8080/accueil)

- Ensuite cliquez sur ce lien [http://localhost:8080/clients](http://localhost:8080/clients) pour visualiser vos clients enregistrés.

![client02.png](images/client02.png)

[Retour vers les exercices](https://pbouget.github.io/cours/framework-back/1-jpa-orm/mapping-orm.html)

[Retour vers le cours complet](https://pbouget.github.io/cours/)