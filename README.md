# Introduction 

Biblioteca (dll) para comunicação com CTIServer para desenvolver CRM utilizando qualquer linguagem 
onde esta dll, métodos e eventos possam ser carregados.

Ferramentas de desenvolvimento

- CSharp

	Microsoft Visual Studio Ultimate 2013
	Version 12.0.40629.00 Update 5
	Microsoft .NET Framework versão 3.5
	Version 4.8.03761
	Installed Version: Ultimate
	
- Delphi

	Borland Delphi Professional
	Versão 5.0 
	Build 6.18
	Service Pack 1

# Getting Started

1.	Installation process : TODO

2.	Software dependencies : TODO

3.	Latest releases

	versão 2.0.17

4.	API references

	# Métodos

		# 4.1 Logon
		
		Logar(StLogar *st)
		
		struct StLogar {
			bool IntervaloCustomizado;
			int Id;
			int Ramal;
			int RamalVirtual;
			int Porta;

			char *IpOrigem;
			char *Departamento;
			char *Senha;
			char *Servidor;
		};
		
		IntervaloCustomizado - Se irá trabalhar com os novos intervalos do CTI.
		
		Id - id do ramal, no caso da plataforma CTI Aculab, este deve ser 0,
			caso a plataforma seja HD, este deve ser o id da posição física do ramal.
		
		Ramal - Ramal a realizar o logon
		
		RamalVirtual - 
		
		Porta - Número da porta tcpip do CTI.
		
		IpOrigem - Endereço ip da máquina do CRM.
		
		Departamento - Departamento do ramal.
		
		Senha - Senha de logon.
		
		Servidor - Endereço ip do CTI.
		
		# 4.2 Deslogar
		
		Deslogar()
		
		# 4.3 Alterar intervalo
		
		AlterarIntervalo(int idIntervalo)
		
		idIntervalo - id do intervalo
		
		# 4.4 Deliga a chamada em andamento
		
		Desligar()
		
		# 4.5 Faz uma chamada
		
		Discar(char *numero, int tipoDiscagem)
		
		numero - Número ou ramal a discar.
		
		tipoDiscagem - 1 = LigacaoExterna, 2 = LigacaoRamal
	
	# Eventos
	
		# 4.1 OnLogado
		
		OnLogado(StLogado *st)
	
		struct StLogado
		{
			int Status;
			int QuantidadeRecados;
			int QuantidadeDialogos;
			int Volume;
			int InterValoExterno;
			int PodeUsarConferencia;
			int RecuperarTodosDialogos;
			int PodeUsarFax;
			int PodeUsarTalkMessager;
			int ApagarDialogo;
			int CategoriaMessager;
			int UsaRotaMenosUm;
			int CategoriasDiscagem;
			int SeGravaConstante;
			int QuantidadeFaxes;
			int Maquina;
			int PodeUsarInterValoExterno;
			int InterValoGrupo;
			int PodeUsarInterValoGrupo;
			int RotaDefault;
			int PodeAcessarVoiceMail;
			int UsaCentroCusto;
			int ValorCentroCusto;
			int CategoriaCentroCusto;
			int InterValoDialer;
			char Mensagem[TAM_MENSAGEM];
			char NomeUsuario[TAM_NOME_USUARIO];
			char NumeroSigaMe[TAM_TELEFONE];
			char RotasDiscagem[TAM_ROTAS_RAMAL];
			char IdRamal[TAM_RAMAL];
		};
		
		# 4.2 OnDeslogado
		
		onDeslogado(StDeslogado *st)
		
		struct StDeslogado
		{
			int Status;
			char Mensagem[TAM_MENSAGEM];
		};
		
		# 4.3 OnInfoIntervaloRamal
		
		OnInfoIntervaloRamal(StInfoIntervaloRamal *st)
		
		struct StInfoIntervaloRamal {
			int RamalStatusDetalheId;
			int Produtivo;
			char Descricao[TAM_DESC_INTERVALO];
		};
		
		# 4.4 OnSetIntervaloRamal
		
		OnSetIntervaloRamal(StSetIntervaloRamal *st)
		
		struct StSetIntervaloRamal {
			int Status;
			int RamalStatusDetalheId;
			char Mensagem[TAM_MENSAGEM];
		};
		
		# 4.5 OnTempoStatus
		
		OnTempoStatus(int t)
		
		# 4.6 OnInfoCliente
		
		OnInfoCliente(const char *s)
		
		# 4.7 OnRingVirtual
		
		OnRingVirtual
		
		# 4.8 OnChamada
		
		OnChamada(StChamada *st)
		
		struct StChamada {
			int Direcao;
			int TipoChamada;
			int CodigoCampanha;

			char Canal[TAM_CANAL_PA];
			char Telefone[TAM_TELEFONE];
			char Servico[TAM_TELEFONE];
			char NomeRamal[TAM_DESC_RAMAL];
			char GlobalId[TAM_GLOBAL_ID];

			char CodigoCliente[TAM_COD_CLIENTE];
			char NomeCliente[TAM_NOME_CLIENTE];
			char InfoAdicional1[TAM_INFO_ADCIONAL];
			char InfoAdicional2[TAM_INFO_ADCIONAL];
			char InfoAdicional3[TAM_INFO_ADCIONAL];
			char InfoAdicional4[TAM_INFO_ADCIONAL];
			char InfoAdicional5[TAM_INFO_ADCIONAL];
		};
		
		# 4.9 OnAtendido
		
		OnAtendido(StChamada *st)
		
		# 4.10 OnChamadaPerdida
		
		OnChamadaPerdida(StChamada *st)
		
		# 4.11 OnDesliga
		
		OnDesliga(StChamada *st)
		
		# 4.12 OnDisca
		
		OnDisca(StChamada *st)
		
		# 4.13 OnDiscaErro
		
		OnDiscaErro(const char *s)
		
		# 4.14 OnPathNomeDialogo
		
		OnPathNomeDialogo(const char *s)
		
	# Tamanho das strings
	
	TAM_IP_ORIGEM           80
	TAM_DEPARTAMENTO        80
	TAM_SENHA               30
	TAM_IP_SERVIDOR         80
	TAM_NOME_USUARIO        100
	TAM_ROTAS_RAMAL         100
	TAM_RAMAL               20
	TAM_MENSAGEM            256
	TAM_TELEFONE            30
	TAM_DESC_INTERVALO      100
	TAM_DESC_RAMAL          100
	TAM_GLOBAL_ID           64
	TAM_COD_CLIENTE         64
	TAM_NOME_CLIENTE        256
	TAM_INFO_ADCIONAL       1024
	TAM_INFO_TEL_IP         80
	TAM_PATH_NOME_ARQ_DIAL  256
	TAM_RECURSO             30
	TAM_CANAL_PA            20
