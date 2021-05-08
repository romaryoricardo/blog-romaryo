---
title: Entendendo Terraform
author: Romaryo Ricardo
date: 2021-05-07 21:08:00 -0300
categories: ["IaC", "Terraform"]
tags: ["IaC", "Terraform"]
toc: false
pin: false
---

Fala Pessoal, tudo bem com vocês?

Nesse post vamos falar um pouco sobre o terraform e seus providers e como ele pode nos ajudar no gerenciamento de nossos ambientes de infraestrutura.

Antes de falar sobre o terraform, é importante que você entenda o conceito de IaC (*Infrastructure as a code*). 


<h2 style="text-align: center">Infraestrutura como Código (IaC) </h2>

 Infraestrutura como código é o processo de provisionamento e gerenciamento automatizado de infraestrutura, utilizando códigos de configurações, evitando assim configurações manuais. resumindo, são os famosos scripts que irão provisionar usa infra para rodar sua aplicação.

### Certo, mas quais os benefícios de utilizar IaC?

Como beneficios podemos citar:

**Agilidade na entrega:** Imagina você ter que entregar a infraestrutura de 3 ambientes, (DEV, HOM e PRD), você faz um único código apenas e provisiona os 3 ambientes. 

**Menor Taxa de Retrabalho:**  Sempre que precisar de ambiente similares aos que já foram criados, basta executar o famoso Ctrl + C e Ctrl + V , copiar, colar, pequenos ajustes e está pronto. legal né ?  Conseguimos centralizar os código também para se tornar reutilizáveis. 🙂 

**Eficiência Operacional:**  Considerando a agilidade para entrega, também temos eficiência, pois ao definir um código, criamos um padrão automatizado, assim reduzindo erros operacionais.

**Versionamento e** **Documentação:** Ao criar sua infra como código, é possível versionar utilizar por exemplo o **Git** gerando um histórico de mudanças, e como na maioria das vezes os códigos são declarativos, também servem como proposito de documentação. Criar a infra e já está documentada. 😆

Agora que entendemos um pouco de IaC, vamos falar sobre o terraform, mas já entenda que terraform te auxilia na implementação do conceito de IaC.
<br/>

<h1 style="text-align: center"> O que é o Terraform? </h1>
Terraform é uma ferramenta que foi desenvolvida em 2012 pela Hashicorp, que permite criar, alterar e versionar sua infraestrutura com segurança e eficiência. Terraform pode gerenciar providers de serviços existentes e populares como as clouds AWS, Azure, GCP e OCI, bem como te permite personalizar soluções internas, criando providers.


### Qual os benefícios de utilizar Terraform?

Ele te dá a maioria dos benefícios da IaC como:

- Agilidade nas entregas
- Redução de erros humanos
- Menos Retrabalho
- Versionamento da infra

E na maioria das vezes pode ser utilizado junto com outras ferramentas como Ansible, Puppet ou Chef para implantação da infraestrutura como código.

Existem outras ferramentas com o mesmo objetivo como o *cloudformation* da AWS, ou *Resource Manager* da Azure, então é ai que entra a vantagem do terraform, com uma única linguagem você consegue provisionar em várias clouds e até no on premisse, isso faz com que o terraform se torne uma ferramenta muito poderosa no que se compromete a fazer.

Já imaginou utilizar a mesma ferramenta para criar sua infra local e na nuvem? 😁

Segue a lista dos providers publicos do terraform: [https://registry.terraform.io/browse/providers](https://registry.terraform.io/browse/providers)

### Mas, o que são providers?

Providers são plugins conectados ao terraform que realizam as interações com os sistemas remotos, assim para provisionar sua infra na cloud será necessário utilizar o provider especifico dessa cloud. 

Sendo um pouco mais técnico, os providers realizam o papel de CRUD ( CREATE, READ, UPDATE e DELETE) nos sistemas remotos, assim eles se tornam responsáveis por saber o que será criado, atualizada ou deletado.

### Então, posso escrever um código terraform e usar em todas as clouds?

O Terraform é **multi provider**, e cada provider possui sua configurações especifica, (cada provider chama uma API diferente), então você terá que escrever um código diferente para cada cloud, não sendo possível que o código escrito para a AWS também crie uma infraestrutura na AZURE, porém dentro do mesmo código conseguimos chamar a AWS e a AZURE e criar recursos nas duas. Ficou muito confuso? 🤔 

Vamos ver um exemplo onde usamos dois provider (OCI - Oracle Cloud Infraestructure e AWS - Amazon Web Services) :


<h1 style="text-align: center;">- - - - -</h1>

![Desktop View](/assets/img/2021-05-07-entendendo-terraform/code-provider-example.png){: width="80%" class="center"} 

<h1 style="text-align: center;">- - - - -</h1>


Neste exemplo, no inicio do código declaramos para o Terraform que vamos usar dois providers, AWS e OCI , e logo depois escrevemos um bloco de códigos referente a AWS e outro referente a OCI, observe que a forma de declarar cada provider muda. e com o mesmo código provisionarmos ambientes em duas clouds. Agora é só usar a criatividade e sair criando seus recursos. 🎉🎊

### Mas, será que preciso ser um desenvolvedor para utilizar o Terraform?

O terraform utiliza uma linguagem chamada HCL (H*ashiCorp configuration language),* é uma linguagem declarativa que você apenas precisa dizer o que será provisionado. Mas uma lógica de programação vai te ajudar a resolver ambientes mais complexos.

<h1 style="text-align: center;">- - - - -</h1>

![Desktop View](/assets/img/2021-05-07-entendendo-terraform/code-example.png){: width="60%" class="center"} 

<h1 style="text-align: center;">- - - - -</h1>

Neste outro exemplo, estamos:

* Declarando o provider da OCI: `provider "oci" {} `

* Criando um recurso de VCN, `resource  "oci_core_vcn" "vcn" {}`

* Exibindo na tela o resultado, `output "show-vcn" {}`

Veja que não é complexo entender um código terraform.


Então pessoal, isso é uma introdução de como funciona o Terraform e seus providers, em breve trarei outros posts mais **hands on**, utilizando o terraform.

Qualquer dúvida, sugestão ou crítica são bem-vindas.


Até a próxima.